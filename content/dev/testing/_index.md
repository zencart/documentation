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
The Test Framework resides within the `not_for_release/testFramework` directory. This directory is only really available
if you `checkout` the Zen Cart code using `git`. It is not available if you just download the Zen Cart code as a zip file 
via a `release` link.

ALERT: Running Zen Cart tests locally has the potential to **overwrite your Zen Cart database and destroy local data.**

FIXME - work in progress

## Initial Setup

1. All of the tests are run using the command-line. If you're on Windows, you need to use the WSL2 (Windows Subsystem for Linux). On Mac, you can use the built-in Terminal, or install iTerm for a more user-friendly terminal experience. On Linux use Terminal.

2. In a new directory, used specifically for running tests, use git to checkout the latest Zen Cart code. This can be done with command-line tools or GUI tools. 

3. Also create a new database specific for testing. The feature-tests below are destructive and will make many changes to the database, so should not be used on a database that you share for a real store. See the Feature Tests section below for how to specify the database in special config files.

## Preparation

To prepare to run the Unit Test and Feature Test suites:

1. Install Composer on your PC:

* go to `getcomposer.org`
* download and install according to your operating system
* follow the Getting Started instructions.

2. Run `composer install` from inside the root directory of your Zen Cart files, on your PC. This will install the base test-tool dependencies.

3. Then, if your PHP version is newer than PHP 8.3+, also run `composer update` to patch the test-tool dependencies to more modern versions.

While probably unnecessary unless upgrading the PHP version, you could re-run `composer update` periodically to grab latest updates of the test-tool dependencies.


## Unit Tests

Unit tests can be run using:

```
composer unit-tests
```

in the root directory of your Zen Cart install.

Currently there are no local configuration requirements needed to run unit tests.

## Feature Tests

(Before running Feature Tests, you will need to set the Feature Test Configuration Files as described in the next section.)

While unit tests allow testing of functions/classes and other small fragments of code, feature tests allow 
testing of the application as a whole. The tests will typically emulate a browser to access the application via URLs and inspect the resulting HTML returned by those URLs.
Feature tests can also interact with the application, by setting form values and submitting those forms.

> NOTE: Current feature tests don't support javascript so interactions with pages that rely on javascript operating may not be possible.
It is planned in the future to allow interactions with pages that rely on javascript using something like `Selenium` or `Panther`.

**WARNING: Feature tests rely on Re-creating the database on each separate test suite. This means it will destroy your database content.**
However, given that you should only be testing on a local development environment, this shouldn't be a problem.

Feature tests can be run using the following in the root directory of your Zen Cart install.

- `composer feature-tests` will run all feature tests
- `composer feature-tests-store` will run feature tests just for the store
- `composer feature-tests-admin` will run feature tests just for the admin


### Configuration for Feature Tests

Feature tests override the standard `configure.php` files used by Zen Cart and require you to create special new configuration files just for testing purposes.

Your configure files should be created in the `not_for_release/testFramework/Support/configs` directory and will be named 
`_USER_.store.configure.php` and `_USER_.admin.configure.php` where the `_USER_` must be replaced by the user that your local environment runs as (ie: the username that you're logged into your PC with).

You can find that `user` by running the following from the root of your installation.

`php ./not_for_release/testFramework/detectUser.php`

These files are exactly the same format as standard Zen Cart `configure.php` files and you can copy the 
`admin.configure.php.example` and `store.configure.php.example` files as starting points.

It is inside these special configure.php files where you will **specify the testing database**.


### Migrations and Seeders

As the functional tests rely on a populated database, the test framework uses the `mysql` install files and demo data found within 
the `zc_install` folder, so this directory needs to be present.

#### Adding extra database content for new tests
There may be times though where you may want to alter the data to test a specific bug. 
An example may be when a search is not finding a product that contains certain strings, 
or a salemaker with specific data is not applying correctly.

In these cases you can create your own data seeder to add this data just for your test.

Custom seeders are created in the `not_for_release/testFramework/Support/database/Seeders/` directory.

An example is `not_for_release/testFramework/Support/database/Seeders/CustomSeeders/StoreWizardSeeder.php`

You can run a custom seeder in your tests using 

`$this->runCustomSeeder('StoreWizardSeeder');`

replacing `StoreWizardSeeder` with the name of your seeder class.

### Mail Server Emulation

**By default the Test Framework disables the sending of emails.** 
This can be overridden by usng another configure file: 
An example exists at `not_for_release/testFramework/Support/configs/main.configure.php.example`

Note: Any misconfiguration here will likely result in failing tests.

As with other configure files noted above the actual configure file should be named 
`_USER_.store.configure.php` with `_USER_` being replaced by the user running the tests.

The example referred to above shows settings for using a local `Mailpit` (an email server emulator) instance, which is an application you would need to install separately.
Yes, you could specify your own real mail server, but beware that when the tests send repeated similar messages they may get falsely treated as spam and may mess with your sender-reputation score. 
Mailtrap.io is a developer-friendly tool with a free-tier to accommodate email testing, and is easy to configure.
{{% /tab %}}
{{< /tabpane >}}
