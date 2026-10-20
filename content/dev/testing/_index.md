---
title: Testing
description: Using the automated tests
aliases:
  - /dev/testframework/
weight: 100
layout: docs
---

{{< tabpane code=false >}}
{{% tab header="v3.x (master)" %}}
The test framework lives in `not_for_release/testFramework`. It is present in the Git repository and is not included in release zip downloads.

Feature tests are destructive. They rebuild and reseed test databases, so do not point them at a real store database.

## Current test stack

- PHPUnit 11 is used for all suites.
- `phpunit.xml` defines three suites: `Unit`, `FeatureStore`, and `FeatureAdmin`.
- Composer installs only development and test dependencies. Zen Cart production bootstrap still uses its own runtime autoloading.
- Feature tests run in-process through helpers under `not_for_release/testFramework/Support/InProcess/`.
- [Infection](https://infection.github.io/) is available for mutation testing of selected classes against the unit tests. It is a developer aid and is not run in CI. See [Mutation testing](#mutation-testing).

## Install dependencies

From the Zen Cart project root:

```bash
composer install
```

That installs PHPUnit and the test-only dependencies declared in `composer.json`.

## Composer commands

The supported Composer scripts are:

- `composer tests-unit`
- `composer tests-feature`
- `composer tests-feature-store`
- `composer tests-feature-admin`
- `composer tests-feature-parallel`
- `composer tests-feature-store-parallel`
- `composer tests-feature-admin-parallel`
- `composer tests-feature-admin-plugin-filesystem`
- `composer tests-plugin`
- `composer tests-ci`
- `composer tests-ci-local`
- `composer tests-db-prepare-workers`
- `composer tests-report-feature-groups`
- `composer tests-report-feature-groups-strict`
- `composer tests-runtime-describe`
- `composer infection`
- `composer infection-fast`

Most runner scripts accept normal PHPUnit arguments after `--`.

The Composer commands are convenience aliases for shell scripts in `not_for_release/testFramework/`. You can also run those scripts directly.

`composer tests-ci` runs the top-level CI-style flow as-is, using the currently resolved environment and test profile.

`composer tests-ci-local` runs the same flow but applies local worker-database defaults when they are not already set, currently:

- `ZC_TEST_DB_BASE_NAME=db`
- `ZC_TEST_DB_WORKERS=2`
- `ZC_TEST_DB_INCLUDE_BASE=0`

`composer tests-db-prepare-workers` is lower-level. It prepares or previews the worker databases expected by the parallel feature runners, but it does not run the test suites itself.

Examples of direct script usage:

```bash
bash not_for_release/testFramework/run-tests-ci.sh
bash not_for_release/testFramework/run-store-feature-tests-ci.sh --filter SearchInProcessTest
bash not_for_release/testFramework/prepare-worker-databases.sh --dry-run
bash not_for_release/testFramework/report-feature-test-groups.sh --summary-only
```

Using Composer is usually the simpler choice:

- shorter commands
- script names are centralized in `composer.json`
- easier for contributors who expect the documented `composer tests-*` entrypoints

Running the scripts directly is useful when you need more control:

- clearer visibility into which underlying runner is being executed
- easier to call a specific shell script while debugging
- convenient in CI or ad-hoc shell automation where you want to bypass the Composer alias layer
- avoids Composer script timeout behavior in environments where Composer is configured with a process time limit

The tradeoff is mostly ergonomics. Composer is easier to remember and document, while direct script execution is more explicit and sometimes easier to debug.

Examples:

```bash
composer tests-unit -- --filter RuntimeConfigTest
composer tests-feature-store -- --filter SearchInProcessTest
composer tests-feature-admin -- --dry-run --filter AdminEndpointsTest
composer tests-plugin -- --plugin gdpr-dsar --suite FeatureAdmin
composer tests-db-prepare-workers -- --dry-run
```

## Unit tests

Run unit tests with:

```bash
composer tests-unit
```

Unit tests live under `not_for_release/testFramework/Unit/` and normally extend:

```php
Tests\Support\zcUnitTestCase
```

`zcUnitTestCase` initializes the unit-test bootstrap for you in `setUp()`.

## Mutation testing

Line coverage tells you which code a test ran, not whether the test would notice if that code were wrong. [Infection](https://infection.github.io/) fills that gap. It makes small changes ("mutants") to the production code, such as removing a concatenated path segment, flipping a comparison, or dropping an `rtrim()`, and re-runs the unit tests. A mutant that no test fails on has "escaped". Each escaped mutant points to behavior that is not pinned down by a test.

Mutation testing is a developer aid for finding gaps while you write tests. It is not run in CI, and the score is not a gate for merging.

### Requirements

Infection needs a code-coverage driver, either PCOV (preferred, much faster) or Xdebug in coverage mode. The `infection/infection` package is installed by `composer install`.

With DDEV, PCOV can be added to the web container with a small override file such as `.ddev/config.pcov.yaml`:

```yaml
webimage_extra_packages: ["php${DDEV_PHP_VERSION}-pcov"]
```

then run `ddev restart`. Run Infection inside the container, for example `ddev composer infection`.

Infection also downloads the PHPUnit XML schema referenced in `phpunit.xml` from `schema.phpunit.de`, so a run fails if that site is unavailable.

### Running it

Run it over the full configured scope:

```bash
composer infection
```

or only over the lines you have changed relative to `master`, which is much quicker and is usually what you want while working on a branch:

```bash
composer infection-fast
```

You can also limit a run to particular source files by passing them as arguments, and pass any other Infection option after `--`:

```bash
composer infection -- includes/classes/Category.php includes/classes/category_tree.php
```

The summary prints in the terminal. Detailed reports, including an HTML report that shows each escaped mutant as a diff, are written to `tmp/infection/`:

- `tmp/infection/infection.html`
- `tmp/infection/infection.log`
- `tmp/infection/summary.log`

A full run over the current scope takes roughly 10 to 15 minutes. Mutants are run in parallel, using four threads by default.

### How it is set up

Configuration lives in `infection.json5` in the project root.

- **Scope.** Infection only mutates an allow-list of files under `includes/classes`. The allow-list is a single regular expression in `source.excludes`, because Infection accepts directories but not individual files as sources. Everything not named in the expression is excluded.
- **Tests.** Infection runs the `Infection` suite defined in `phpunit.xml`, not the whole `Unit` suite. The full unit suite cannot share one PHPUnit process (see the notes on global constants and function declarations above), so the `Infection` suite lists the test directories that cover the mutated classes and runs with `--process-isolation`.
- **Coverage.** The Composer scripts pass `--only-covering-test-cases`, so each mutant is tested only by the tests that cover it.
- **Bootstrap.** Infection loads the classes it mutates in its own process, which does not run the PHPUnit bootstrap. `not_for_release/testFramework/Support/infection-bootstrap.php` defines the constants some classes need in order to load, for example `IS_ADMIN_FLAG`.
- **Thresholds.** `minMsi` and `minCoveredMsi` are set slightly below the current score so that a regression is flagged. The MSI (Mutation Score Indicator) is the percentage of mutants that were detected.

### Adding a class to the scope

1. Make sure the class has unit tests that run reliably, and that they are in a test directory included in the `Infection` suite in `phpunit.xml`. Add the directory if it is not.
2. Add the file or directory to the allow-list expression in `source.excludes` in `infection.json5`.
3. Run Infection against just that file to get a baseline, then work through the escaped mutants.

### Working through escaped mutants

Open `tmp/infection/infection.html` or the log and read the diff for each escaped mutant. Typical fixes:

- Assert the exact value, path, or SQL string a method builds, not just that it returns something.
- Test both sides of a condition, including boundary values and empty inputs.
- Check ordering and de-duplication of lists, and that array keys are re-indexed.
- Call protected methods through a test subclass or a bound closure, so that a mutant that narrows their visibility is detected.

Not every escaped mutant is a real gap. Some are equivalent, meaning the changed code behaves identically, for example an extra `rtrim()` whose effect is repeated by the next step, or an early `return` on an empty array. Review each one and move on when it cannot be observed. Do not add contrived tests just to raise the score.

### Test helpers

Two helpers under `not_for_release/testFramework/Support/` make it easier to unit test classes that use the global `$db`:

- `Tests\Support\ScriptedDatabase` is a trait that replaces `$db` with a mocked `queryFactory`. Register responses with `respondTo($regex, $rows)`; the first matching pattern wins. Executed SQL is recorded so a test can assert on the exact statement and on the limit, cache flag, and cache lifetime passed to `Execute()`.
- `Tests\Support\InMemoryTemplateSelectDatabase` is a trait that models the `template_select` table in memory for the `TemplateSelect` tests.

## Feature tests

Feature tests exercise the application through Zen Cart's bootstrap, request handling, database setup, and HTML responses.

Current feature suites live in:

- `not_for_release/testFramework/FeatureStore`
- `not_for_release/testFramework/FeatureAdmin`

Run them with:

```bash
composer tests-feature
composer tests-feature-store
composer tests-feature-admin
```

Useful behaviors of the current runners:

- `composer tests-feature-store` prints the resolved runtime, validates feature grouping, prepares worker databases, then runs storefront parallel tests.
- `composer tests-feature-admin` does the same for admin tests, then also runs admin `plugin-filesystem` buckets.
- `composer tests-feature` runs the aggregate storefront/admin parallel flow plus plugin-filesystem buckets.
- `--dry-run` shows what would run without mutating the databases.

### Base classes

For new feature tests, use these base classes:

- `Tests\Support\zcInProcessFeatureTestCaseStore`
- `Tests\Support\zcInProcessFeatureTestCaseAdmin`

The compatibility aliases below still exist, but the in-process classes are the current implementation:

- `Tests\Support\zcFeatureTestCaseStore`
- `Tests\Support\zcFeatureTestCaseAdmin`
- `Tests\Support\zcFeatureTestCase`

The storefront base class provides helpers like `get()`, `post()`, `getMainPage()`, `visitLogin()`, `visitCart()`, and redirect/cookie handling.

The admin base class provides helpers like `getAdmin()`, `postAdmin()`, `visitAdminHome()`, `visitAdminCommand()`, `submitAdminLogin()`, and `submitAdminForm()`.

### Feature test grouping

The current shell runners use PHPUnit groups to decide what can run in parallel.

- Tag parallel-safe feature tests with `parallel-candidate`.
- Tag filesystem-mutating plugin tests with `plugin-filesystem`.
- Use `serial` together with `plugin-filesystem` when the test must not run concurrently.

Example with PHPUnit 11 attributes:

```php
#[\PHPUnit\Framework\Attributes\Group('parallel-candidate')]
final class SearchInProcessTest extends \Tests\Support\zcInProcessFeatureTestCaseStore
{
}
```

```php
#[\PHPUnit\Framework\Attributes\Group('serial')]
#[\PHPUnit\Framework\Attributes\Group('plugin-filesystem')]
final class BasicPluginInstallTest extends \Tests\Support\zcInProcessFeatureTestCaseAdmin
{
}
```

Use:

```bash
composer tests-report-feature-groups
composer tests-report-feature-groups-strict
```

to inspect or enforce grouping coverage.

### Understanding the group report

`composer tests-report-feature-groups` prints both explicit grouping tags and a few heuristic shared-state signals.

Common report sections:

- `Tagged serial`: feature tests explicitly marked `serial`.
- `Tagged plugin-filesystem`: feature tests explicitly marked `plugin-filesystem`.
- `Tagged parallel-candidate`: feature tests explicitly marked `parallel-candidate`.
- `Untagged files`: feature tests with none of the expected explicit grouping tags.
- `Plugin-local feature test files`: feature tests discovered under `zc_plugins/*/*/tests/FeatureStore` or `zc_plugins/*/*/tests/FeatureAdmin`.
- `Suite breakdown`: per-suite totals for store and admin tests, including how many are serial, parallel-candidate, or untagged.
- `Invalid explicit group combinations`: files with conflicting or incomplete explicit tags, such as `serial` together with `parallel-candidate`, or `plugin-filesystem` without `serial`.

The report also includes heuristic sections. These are grep-style indicators, not perfect proofs:

- `Heuristic direct DB writers`: files containing direct calls such as `TestDb::insert()`, `TestDb::update()`, or `TestDb::truncate()`.
- `Heuristic custom seeder users`: files calling `runCustomSeeder()`.
- `Heuristic filesystem writers`: files that appear to mutate plugin or filesystem state, such as plugin installation/removal helpers or direct file writes like `touch()`, `file_put_contents()`, or `unlink()`.

These heuristic buckets are there to highlight tests that may need `serial` treatment or closer review. They can miss some shared-state behavior and they can also over-report harmless matches.

`composer tests-report-feature-groups-strict` is the stricter form used by the runners. It fails when feature test files are untagged or when explicit grouping combinations are invalid.

## Configuration and environment

The current framework still uses test configure profiles named by user or runtime, such as `<user>.store.configure.php`, `<user>.admin.configure.php`, `ddev.store.configure.php`, or `runner.store.configure.php`.

Instead, runner settings are resolved from:

- environment variables already exported in your shell or CI job
- the active Zen Cart test profile, resolved from the test configure files when DB settings are not overridden

Environment values exported in the shell or CI job override the database defaults derived from the active test profile.

Useful variables:

- `ZC_TEST_DB_HOST`
- `ZC_TEST_DB_PORT`
- `ZC_TEST_DB_USER`
- `ZC_TEST_DB_PASSWORD`
- `ZC_TEST_DB_BASE_NAME`
- `ZC_TEST_DB_WORKERS`
- `ZC_TEST_DB_INCLUDE_BASE`
- `ZC_TEST_USE_MAILSERVER`
- `ZC_TEST_MAILSERVER_HOST`
- `ZC_TEST_MAILSERVER_PORT`
- `ZC_TEST_MAILSERVER_USER`
- `ZC_TEST_MAILSERVER_PASSWORD`
- `ZC_PARALLEL_PROCESSES`
- `ZC_TEST_PROGRESS_INTERVAL`

To inspect the effective runtime configuration:

```bash
composer tests-runtime-describe
```

That command reports the resolved config profile, config files, worker token, database name, log directory, artifact directories, and plugin directory.

### Test configure files

Feature bootstrap still loads dedicated test configure files through `not_for_release/testFramework/Support/application_testing.php`.

The resolver looks in `not_for_release/testFramework/Support/configs/` for the active test config profile and loads:

- `runner.main.configure.php`
- `runner.store.configure.php`
- `runner.admin.configure.php`

Those files provide the runtime-specific `configure.php` values used during feature-test bootstrap.

## Databases, logs, and artifacts

Prepare worker databases explicitly with:

```bash
composer tests-db-prepare-workers
```

The MySQL user used for feature-test database preparation should normally have permission to create and drop databases, because the worker-database setup may issue `DROP DATABASE` and `CREATE DATABASE` statements.

If your test user does not have those privileges, pre-create the worker databases with a privileged MySQL user before running the feature suite.

Preview the database plan without changing MySQL:

```bash
composer tests-db-prepare-workers -- --dry-run
```

Current feature runners also call worker-database preparation automatically before they execute tests.

Logs and artifacts are written under `not_for_release/testFramework/logs/`. The runtime helper also reports the resolved artifact directories for storefront and admin tests.

## Plugin-local tests

Plugins can keep tests inside their own versioned directory:

```text
zc_plugins/<PluginName>/<version>/tests
```

Supported suite layout:

- `tests/Unit`
- `tests/FeatureStore`
- `tests/FeatureAdmin`

Recommended plugin-local base classes:

- `Tests\Support\zcUnitTestCase`
- `Tests\Support\zcInProcessFeatureTestCaseStore`
- `Tests\Support\zcInProcessFeatureTestCaseAdmin`

Run all plugin-local tests:

```bash
composer tests-plugin
```

Run a single plugin or suite:

```bash
composer tests-plugin -- --plugin gdpr-dsar
composer tests-plugin -- --plugin gdpr-dsar --suite FeatureStore
composer tests-plugin -- --plugin gdpr-dsar --suite FeatureAdmin
composer tests-plugin -- --plugin gdpr-dsar --suite Unit
```

Run only plugin-local filesystem-mutation tests:

```bash
composer tests-plugin -- --plugin gdpr-dsar --require-group plugin-filesystem --group plugin-filesystem
```

## Seeders and database customization

The framework bootstraps feature databases from the install SQL and test support seeders. Custom seeders live in:

```text
not_for_release/testFramework/Support/database/Seeders/
```

Seeder classes are autoloaded with the `Seeders\` namespace and must implement `Tests\Services\Contracts\TestSeederInterface`.

Use a custom seeder when a test needs database state beyond the standard bootstrap, for example:

- a specific configuration value
- extra products, coupons, or tax data
- a setup sequence that would be noisy or repetitive to build inline in every test

The seeder interface is simple:

```php
namespace Tests\Services\Contracts;

interface TestSeederInterface
{
    public function run(array $parameters = []): void;
}
```

A typical seeder updates or inserts rows using `Tests\Support\Database\TestDb`.

Example:

```php
<?php

namespace Seeders;

use Tests\Services\Contracts\TestSeederInterface;
use Tests\Support\Database\TestDb;

class StoreWizardSeeder implements TestSeederInterface
{
    public function run(array $parameters = []): void
    {
        TestDb::update(
            'configuration',
            ['configuration_value' => 'Zencart Store Name'],
            'configuration_key = :config_key',
            [':config_key' => 'STORE_NAME']
        );

        TestDb::update(
            'configuration',
            ['configuration_value' => 'Zencart Store Owner'],
            'configuration_key = :config_key',
            [':config_key' => 'STORE_OWNER']
        );
    }
}
```

From a test case that uses the database concerns helpers, run a custom seeder with:

```php
self::runCustomSeeder('StoreWizardSeeder');
```

That call resolves the class as `Seeders\StoreWizardSeeder` and executes its `run()` method.

A typical usage pattern in a feature test looks like this:

```php
final class ExampleStoreTest extends \Tests\Support\zcInProcessFeatureTestCaseStore
{
    public function test_store_uses_seeded_configuration(): void
    {
        self::runCustomSeeder('StoreWizardSeeder');

        $response = $this->get('/');

        $response->assertOk();
        $response->assertSee('Zencart Store Name');
    }
}
```

Keep seeders focused and test-specific. If a seeder becomes broadly useful across many tests, give it a descriptive name and keep the setup logic reusable rather than embedding one-off assertions or test flow inside the seeder itself.

## Container-based runs

The preferred repeatable CI runtime is the published test-runner container:

```text
ghcr.io/zencart/zencart-test-runner
```

Example:

```bash
docker run --rm \
  -v "$PWD:/var/www/html" \
  -w /var/www/html \
  ghcr.io/zencart/zencart-test-runner:php-8.4 \
  composer tests-unit
```

The container supplies PHP and tooling. Zen Cart source code is still mounted from your checkout.

## Notes

- Unit tests do not require the feature-test database setup.
- Feature tests do not run browser JavaScript.
- The `zc_install` directory must be present for database bootstrap and demo-data loading.
{{% /tab %}}
{{% tab header="v2.x" %}}
This tab describes the test framework as it exists on the `2.2` branch (and `2.1`, where noted). The framework lives in `not_for_release/testFramework` and is only present if you clone the Zen Cart repository with `git`. It is not included in release zip downloads.

> **Warning:** Feature tests rebuild the database they are pointed at, on every test class. Never point them at a database that holds real store data. Use a dedicated test database.

## How it works

- **PHPUnit 9** runs three suites, defined in `phpunit.xml`: `Unit`, `FeatureStore` and `FeatureAdmin`.
- **Unit tests** run in the PHPUnit process with `--process-isolation`. They need no database and no web server.
- **Feature tests** drive a real, running copy of Zen Cart over HTTP using Symfony's `HttpBrowser`. The test code fetches pages and submits forms from `HTTP_SERVER`, and checks the HTML that comes back. They do not run JavaScript.
- Before each feature test class, the framework drops and rebuilds the test database from `zc_install/sql/install/mysql_zencart.sql`, `mysql_utf8.sql` and `sql/demo/mysql_demo.sql`, and then runs the `InitialSetupSeeder`. Every test class therefore starts from the same demo-data store, and the `zc_install` directory must be present.
- The web server that serves `HTTP_SERVER` and the PHPUnit process both need to read the same database settings. When the web server receives a request from the test browser (or is started with the environment variable `ZENCART_TESTFRAMEWORK_RUNNING=1`), Zen Cart loads a test configure file in place of `includes/configure.php`.

## Initial setup

1. Run everything from the command line. On Windows use WSL2. On macOS and Linux use the normal terminal.
2. Use a separate clone of the Zen Cart repository for testing, at the branch you want to test.
3. Create an empty database for testing. The database user needs permission to drop and create tables in it.
4. Have a web server serving the clone at a URL you will set as `HTTP_SERVER` in the configure files below. Two common choices:
   - **DDEV**: the framework recognises a DDEV project automatically. Its example configure files use `https://zencart.ddev.site`, database host `db`, and user, password and database name of `root`, `root` and `db`.
   - **PHP's built-in server**, which is what the GitHub Actions workflows use (see [Using the PHP built-in server](#using-the-php-built-in-server)).

## Installing the test tools

1. Install [Composer](https://getcomposer.org/).
2. From the root of the clone, run:

   ```bash
   composer install
   ```

   This installs PHPUnit, Symfony BrowserKit, HttpClient and the other test-only dependencies from `composer.json`.

3. If your PHP version is 8.4 or newer and the install fails, or tests fail with errors from inside `vendor`, run `composer update` to move the test tools to newer versions. Running it again from time to time is also a reasonable way of picking up updates.

## Running the tests

| Command | Runs |
| --- | --- |
| `composer unit-tests` | The `Unit` suite only |
| `composer feature-tests` | `FeatureStore` and `FeatureAdmin` together |
| `composer feature-tests-store` | Storefront feature tests |
| `composer feature-tests-admin` | Admin feature tests |

Each is a shortcut in `composer.json` for a `phpunit --testsuite ...` command. You can also call PHPUnit directly, which is useful for running one test class or method:

```bash
vendor/bin/phpunit --testsuite FeatureStore --filter CreateAccountTest
vendor/bin/phpunit --testsuite Unit --process-isolation --filter DiscountCouponsTest
```

Logs written by the application during a test run are copied to `not_for_release/testFramework/logs/console/store/` or `.../admin/`, which is also what the CI jobs upload as artifacts when a run fails.

## Unit tests

Unit tests live in `not_for_release/testFramework/Unit/`, in a directory per area (for example `testsCategories/` and `testsNotifiers/`). Test files must end in `Test.php`.

Extend `Tests\Support\zcUnitTestCase`. Its `setUp()` defines the constants and loads the files a test needs to run Zen Cart classes on their own (paths, `database_tables.php`, `filenames.php`, a notifier instance and the polyfills), so call `parent::setUp()` first. It also provides `mockIterator()` and `assertURLGenerated()`.

```php
namespace Tests\Unit\testsExample;

use Tests\Support\zcUnitTestCase;

class ExampleTest extends zcUnitTestCase
{
    public function setUp(): void
    {
        parent::setUp();
        require_once DIR_FS_CATALOG . DIR_WS_CLASSES . 'category_tree.php';
    }

    public function testSomething()
    {
        $this->assertTrue(true);
    }
}
```

No local configuration is needed to run unit tests. The CI job only creates an empty `includes/configure.php` first.

## Feature tests

### Configure files

Feature tests need configure files that tell Zen Cart which URL, directory and database to use during a test run. Put them in `not_for_release/testFramework/Support/configs/`. They are ignored by git.

You need one file for each of these contexts:

| File | Used by |
| --- | --- |
| `<name>.store.configure.php` | The storefront, and `FeatureStore` tests |
| `<name>.admin.configure.php` | The admin, and `FeatureAdmin` tests |
| `<name>.main.configure.php` | The test runner itself (optional, see [Mail server](#mail-server-emulation)) |

Copy `store.configure.php.example` and `admin.configure.php.example` as starting points. They have the same format as the normal Zen Cart `configure.php` files. Set at least `HTTP_SERVER` (and `HTTPS_SERVER` for the store), `DIR_FS_CATALOG` and the `DB_*` settings. **The test database is specified here.** The store and admin files must use the same database.

**Choosing `<name>`**

- On the `2.2` branch the framework looks for files for these names, in this order: your login user, then `ddev`, then `runner`. Under DDEV the user is always `ddev`. To see which user the framework detects:

  ```bash
  php not_for_release/testFramework/detectUser.php
  ```

- For each name, it first looks for a file specific to the branch you are on, and then for the generic one. For example, on `2.2` it tries `ddev.2.2.store.configure.php` and then `ddev.store.configure.php`. This lets one working copy keep separate settings for several branches. The branch is taken from the environment variables `ZENCART_TESTFRAMEWORK_BRANCH_FAMILY`, `ZENCART_TESTFRAMEWORK_BASE_BRANCH` or `GITHUB_BASE_REF`, otherwise from your checked-out branch if it is `master` or `2.2`, otherwise from whichever of those two is nearest in the git history. Set `ZENCART_TESTFRAMEWORK_BRANCH_CANDIDATES` (default `master,2.2`) to change the branches considered.
- The `runner.*.configure.php` files are committed to the repository for GitHub Actions. They use `127.0.0.1` for the database and `HTTP_SERVER` from the environment, but `DIR_FS_CATALOG` is a GitHub runner path. Do not use them locally without changing that. Create your own files instead.
- On the `2.1` branch there is no fallback and no branch matching. The files must be named exactly `<user>.store.configure.php` and so on, where `<user>` is the value from `detectUser.php` (`ddev` under DDEV).

If no matching file is found the tests stop with a message naming the directory they searched.

### Using the PHP built-in server

You do not need Apache or DDEV. In one terminal, start the server from the root of the clone:

```bash
HTTP_SERVER=http://localhost:8000 \
ZENCART_TESTFRAMEWORK_RUNNING=1 \
ZENCART_TESTFRAMEWORK_CONFIG_USER=<name> \
php -d auto_prepend_file="$PWD/not_for_release/testFramework/Support/php_server_prepend.php" \
    -S localhost:8000 -t .
```

where `<name>` is the prefix of your configure files. In another terminal run the tests with `HTTP_SERVER=http://localhost:8000` set in the environment. This is the same sequence as in `.github/workflows/zc_feature_test_store_suite.yml`, which you can copy from.

### Writing a feature test

Feature tests live in `not_for_release/testFramework/FeatureStore/` and `FeatureAdmin/`. Extend the matching base class:

- `Tests\Support\zcFeatureTestCaseStore`
- `Tests\Support\zcFeatureTestCaseAdmin`

They provide `$this->browser` (a Symfony `HttpBrowser` with cookie support), and helper methods from these traits, which they already use:

| Trait | Helpers |
| --- | --- |
| `GeneralConcerns` | `buildStoreLink($page)`, `buildAdminLink($cmd)`, `browserAdminLogin()`, `locateElementInPageSource()`, and the plugin file helpers `installPluginToFilesystem()` and `removePlugin()` |
| `CustomerAccountConcerns` | `createCustomerAccountOrLogin($profile)`, `loginCustomer()`, `logoutCustomer()`, gift voucher and group-discount setup |
| `ConfigurationSettingsConcerns` | `setConfiguration($key, $value)`, `getConfigurationSetting($key)`, and switches for tax-inclusive pricing and shipping tax |
| `DiscountCouponConcerns` | `createCoupon($profile)` |
| `LowOrderFeeConcerns` | `switchLowOrderFee($mode)` |
| `LogFileConcerns` | `logFilesExists()` |

Customer and admin details come from named profiles in `Support/helpers/ProfileManager.php`, such as `florida-basic1` or `admin`. The admin login is `Admin` / `password`.

For direct database checks use `Tests\Support\Database\TestDb` (`selectOne()`, `selectValue()`, `insert()`, `update()`, `truncate()`). It uses prepared statements and is available on `2.2`. On `2.1`, tests query the database through Eloquent models (for example `App\Models\Customer`) instead.

```php
namespace Tests\FeatureStore\CreateAccount;

use Tests\Support\Database\TestDb;
use Tests\Support\Traits\CustomerAccountConcerns;
use Tests\Support\zcFeatureTestCaseStore;

class CreateAccountTest extends zcFeatureTestCaseStore
{
    use CustomerAccountConcerns;

    public function testCreateAccount()
    {
        $profile = $this->createCustomerAccountOrLogin('florida-basic1');

        $customer = TestDb::selectOne(
            'SELECT customers_firstname FROM customers WHERE customers_email_address = :email LIMIT 1',
            [':email' => $profile['email_address']]
        );
        $this->assertSame($profile['firstname'], $customer['customers_firstname']);
    }
}
```

To check a page directly, use the browser:

```php
$this->browser->request('GET', $this->buildStoreLink('shopping_cart'));
$this->assertEquals(200, $this->browser->getResponse()->getStatusCode());
```

### Seeders

Custom seeders add or change database rows for one test. They live in `not_for_release/testFramework/Support/database/Seeders/` in the `Seeders` namespace, with a `run()` method. Run one from a test:

```php
$this->runCustomSeeder('StoreWizardSeeder');
```

Replace `StoreWizardSeeder` with the name of your class. Existing seeders include `StoreWizardSeeder` (store name and owner), `CouponTableSeeder`, `CompoundTaxesSeeder` and `DisplayLogsSeeder`.

```php
namespace Seeders;

use Tests\Support\Database\TestDb;

class MySeeder
{
    public function run()
    {
        TestDb::update(
            'configuration',
            ['configuration_value' => 'My Test Store'],
            'configuration_key = :config_key',
            [':config_key' => 'STORE_NAME']
        );
    }
}
```

### Mail server emulation

By default the framework disables sending of email. A `main` configure file can switch on an SMTP test server, for example [Mailpit](https://mailpit.axllc.net/) (included with DDEV). It returns an array:

```php
<?php
return [
    'use-server' => true,
    'use-mailserver' => true,
    'mailserver-host' => 'localhost',
    'mailserver-port' => 1025,
    'mailserver-user' => 'ddev',
    'mailserver-password' => 'mailpit',
];
```

Save it as `<name>.main.configure.php`. The committed `runner.main.configure.php` shows the same keys with `use-mailserver` set to `false`. In the `2.2` set-up code both `use-server` and `use-mailserver` must be present and true, which is why the example sets both. A wrong setting here usually shows up as failing tests. Avoid pointing it at a real mail server, since repeated similar test messages may get flagged as spam.

### Plugin tests

`FeatureAdmin/PluginTests/` shows how to test plugin installation. The sample plugin used is in `Support/plugins/zenTestPlugin/`. A test copies it into `zc_plugins/` with `installPluginToFilesystem()` and removes it with `removePlugin()`.

## Running in CI

The repository has three GitHub Actions workflows, `zc_unit_test_suite.yml`, `zc_feature_test_store_suite.yml` and `zc_feature_test_admin_suite.yml`. They run against several PHP versions, start MySQL as a service, start the built-in PHP server with the `runner` profile, and then run the relevant suite. Use them as a reference for setting up your own CI.

## Troubleshooting

- **"could not find config file" or "No test config file found"**: there is no configure file for your user, branch and context. Check the name against the list in [Configure files](#configure-files).
- **Feature tests fail straight away with connection errors**: `HTTP_SERVER` in your store and admin configure files is not reachable from where PHPUnit runs, or the web server is not running.
- **Database errors during set-up**: the database user cannot drop or create tables, or the store and admin configure files use different databases.
- **Pages work but data is missing**: the framework rebuilds the database for each test class. A test that needs extra data should set it up itself, with a seeder or with `TestDb`.
{{% /tab %}}
{{< /tabpane >}}
