---
title: Test Framework
description: Using the automated tests
weight: 300
layout: docs
---

The test framework lives in `not_for_release/testFramework`. It is present in the Git repository and is not included in release zip downloads.

Feature tests are destructive. They rebuild and reseed test databases, so do not point them at a real store database.

## Current test stack

- PHPUnit 11 is used for all suites.
- `phpunit.xml` defines three suites: `Unit`, `FeatureStore`, and `FeatureAdmin`.
- Composer installs only development and test dependencies. Zen Cart production bootstrap still uses its own runtime autoloading.
- Feature tests run in-process through helpers under `not_for_release/testFramework/Support/InProcess/`.

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
