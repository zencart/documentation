---
title: Test Framework
description: Using the automated tests
weight: 300
layout: docs
---

The Test Framework resides within the `not_for_release/testFramework` directory. This directory is only available if you
checkout the Zen Cart code using `git`. It is not available if you download the Zen Cart code as a zip file via a release
link.

ALERT: Running Zen Cart tests locally has the potential to **overwrite your Zen Cart database and destroy local data.**

The preferred repeatable runtime for CI and plugin testing is the Zen Cart test-runner container published to GitHub
Container Registry:

```text
ghcr.io/zencart/zencart-test-runner
```

The container provides PHP, Composer, required PHP extensions, MySQL client tooling, and shell utilities. The container does
not contain Zen Cart source code; you mount or checkout the Zen Cart repository into the container.

## Initial Setup

1. All of the tests are run using the command-line. If you're on Windows, you need to use the WSL2 (Windows Subsystem for Linux). On Mac, you can use the built-in Terminal, or install iTerm for a more user-friendly terminal experience. On Linux use Terminal.

2. In a new directory, used specifically for running tests, use git to checkout the latest Zen Cart code. This can be done with command-line tools or GUI tools. 

3. Also create a new database specific for testing. The feature-tests below are destructive and will make many changes to the database, so should not be used on a database that you share for a real store. See the Feature Tests section below for how to specify the database in special config files.

4. If you want the container-based runtime, install Docker and pull the PHP version you want to test against:

```bash
docker pull ghcr.io/zencart/zencart-test-runner:php-8.4
```

## Preparation

To prepare to run the Unit Test and Feature Test suites on your host machine:

1. Install Composer on your PC:

* go to `getcomposer.org`
* download and install according to your operating system
* follow the Getting Started instructions.

2. Run `composer install` from inside the root directory of your Zen Cart files, on your PC. This will install the base test-tool dependencies.

3. Then, if your PHP version is newer than PHP 8.3+, also run `composer update` to patch the test-tool dependencies to more modern versions.

While probably unnecessary unless upgrading the PHP version, you could re-run `composer update` periodically to grab latest updates of the test-tool dependencies.

When using the container, run Composer inside the image instead:

```bash
docker run --rm \
  -v "$PWD:/var/www/html" \
  -w /var/www/html \
  ghcr.io/zencart/zencart-test-runner:php-8.4 \
  composer install
```

## Composer Test Commands

All supported Composer test commands now start with `tests-`.

Common commands:

- `composer tests-unit` runs the unit tests.
- `composer tests-feature` runs the aggregate feature-test flow.
- `composer tests-feature-store` runs storefront feature-test buckets.
- `composer tests-feature-admin` runs admin feature-test buckets.
- `composer tests-plugin` discovers and runs plugin-local tests under `zc_plugins/<PluginName>/<version>/tests`.
- `composer tests-ci` runs the top-level CI-style unit and feature flow.
- `composer tests-ci-local` runs the top-level CI-style flow with local worker database defaults.
- `composer tests-report-feature-groups` reports feature-test grouping.
- `composer tests-report-feature-groups-strict` fails if feature-test grouping is incomplete or contradictory.
- `composer tests-db-prepare-workers` prepares the base and worker databases used by parallel feature tests.
- `composer tests-runtime-describe` prints the derived database, log, progress, artifact, and plugin paths for the current environment.

Most runners accept normal PHPUnit arguments after `--`.

Examples:

```bash
composer tests-unit -- --filter RuntimeConfigTest
composer tests-feature -- --dry-run --filter BasicPluginInstallTest
composer tests-feature-store -- --filter SearchInProcessTest
composer tests-plugin -- --plugin gdpr-dsar
```

Inside the test-runner container, the command shape is the same:

```bash
docker run --rm \
  -v "$PWD:/var/www/html" \
  -w /var/www/html \
  ghcr.io/zencart/zencart-test-runner:php-8.4 \
  composer tests-unit
```

## Unit Tests

Unit tests can be run using:

```
composer tests-unit
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

- `composer tests-feature` will run the aggregate feature-test flow.
- `composer tests-feature-store` will run storefront feature-test buckets.
- `composer tests-feature-admin` will run admin feature-test buckets.
- `composer tests-feature -- --dry-run` will preview the selected feature-test buckets without executing them.
- `composer tests-feature-parallel` will run the lower-level aggregate parallel feature runner.


### Configuration for Feature Tests

Feature tests override the standard `configure.php` files used by Zen Cart.

The current test runner includes runner configuration files in:

```text
not_for_release/testFramework/Support/configs
```

The runner can also load environment files from:

```text
not_for_release/testFramework/Support/configs/test-runner.env
not_for_release/testFramework/Support/configs/test-runner.local.env
```

Use these files or environment variables to control database host, port, user, password, worker database settings, and
optional test mailserver settings.

Useful environment variables include:

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

Values already set in the shell or CI environment take precedence over values in the environment files. If both
`test-runner.env` and `test-runner.local.env` exist, `test-runner.local.env` is loaded after `test-runner.env` and can
override local defaults.

For example, to send feature-test email through Mailpit in a DDEV-style environment, add this to
`not_for_release/testFramework/Support/configs/test-runner.local.env`:

```bash
ZC_TEST_USE_MAILSERVER=true
ZC_TEST_MAILSERVER_HOST=mailpit
ZC_TEST_MAILSERVER_PORT=1025
ZC_TEST_MAILSERVER_USER=ddev
ZC_TEST_MAILSERVER_PASSWORD=mailpit
```

When `ZC_TEST_USE_MAILSERVER` is enabled, the test database bootstrap enables email sending and seeds Zen Cart's email
configuration to use the configured SMTP catcher.

You can preview the resolved runtime settings with:

```bash
composer tests-runtime-describe
```

Prepare worker databases with:

```bash
composer tests-db-prepare-workers
```

Preview the planned database changes without mutating MySQL:

```bash
composer tests-db-prepare-workers -- --dry-run
```

Older checkouts may still use user-specific configure files. In those checkouts, feature tests require special new
configuration files just for testing purposes.

Your configure files should be created in the `not_for_release/testFramework/Support/configs` directory and will be named 
`_USER_.store.configure.php` and `_USER_.admin.configure.php` where the `_USER_` must be replaced by the user that your local environment runs as (ie: the username that you're logged into your PC with).

You can find that `user` by running the following from the root of your installation.

`php ./not_for_release/testFramework/detectUser.php`

These files are exactly the same format as standard Zen Cart `configure.php` files and you can copy the 
`admin.configure.php.example` and `store.configure.php.example` files as starting points.

It is inside these special configure.php files where you will **specify the testing database**.

## Plugin-Local Tests

Plugins can keep tests with the plugin under:

```text
zc_plugins/<PluginName>/<version>/tests
```

Recommended plugin-local layout:

- `tests/FeatureAdmin/*Test.php` for admin feature tests.
- `tests/FeatureStore/*Test.php` for storefront feature tests.
- `tests/Unit/*Test.php` for isolated unit tests.
- `tests/Fixtures/` for plugin-owned fixtures.
- `tests/Seeders/` for plugin-owned seeders.
- `tests/bootstrap.php` for optional plugin bootstrap code.
- `tests/plugin-test.php` for optional plugin test metadata.

Plugin-local tests should extend the normal Zen Cart test framework base classes:

- `Tests\Support\zcInProcessFeatureTestCaseAdmin`
- `Tests\Support\zcInProcessFeatureTestCaseStore`
- `Tests\Support\zcUnitTestCase`

Run all plugin-local tests:

```bash
composer tests-plugin
```

Run tests for one plugin:

```bash
composer tests-plugin -- --plugin gdpr-dsar
```

Run one plugin and suite:

```bash
composer tests-plugin -- --plugin gdpr-dsar --suite FeatureAdmin
composer tests-plugin -- --plugin gdpr-dsar --suite FeatureStore
composer tests-plugin -- --plugin gdpr-dsar --suite Unit
```

Run plugin-local filesystem mutation tests:

```bash
composer tests-plugin -- --plugin gdpr-dsar --require-group plugin-filesystem --group plugin-filesystem
```

Plugin-local tests that install, uninstall, enable, disable, or mutate plugin filesystem state should be tagged:

```php
/**
 * @group serial
 * @group plugin-filesystem
 */
```

Read-only plugin-local tests can use:

```php
/**
 * @group parallel-candidate
 */
```

Plugin repositories should run plugin-local tests by checking out Zen Cart, copying the plugin into
`zc_plugins/<PluginName>/<version>`, and running `composer tests-plugin` inside the published test-runner container.

The container is version-neutral. The Zen Cart version under test is selected by the Git checkout ref; the PHP version is
selected by the container tag.

For example:

```text
PHP version      -> ghcr.io/zencart/zencart-test-runner:php-8.4
Zen Cart version -> actions/checkout ref
Plugin version   -> zc_plugins/<PluginName>/<version>
```

## Plugin GitHub Actions

A plugin repository can run its own tests by checking out Zen Cart during the workflow, installing the plugin into the
checked-out Zen Cart tree, and then running Zen Cart's `composer tests-plugin` command inside the published test-runner
container.

The plugin repository should contain only plugin-owned files:

```text
manifest.php
catalog/
admin/
Installer/
tests/
.github/workflows/plugin-tests.yml
```

The workflow should create this runtime layout:

```text
workspace/
  plugin/
  zencart/
    composer.json
    not_for_release/testFramework/
    zc_plugins/
      gdpr-dsar/
        v1.0.2/
          manifest.php
          catalog/
          admin/
          Installer
          tests/
```

Use workflow environment variables for plugin and Zen Cart targeting so releases are easy to update:

```yaml
env:
  ZC_CORE_REPOSITORY: zencart/zencart
  ZC_CORE_REF: master
  ZC_PLUGIN_NAME: gdpr-dsar
  ZC_PLUGIN_VERSION: v1.0.2
  ZC_TEST_RUNNER_IMAGE: ghcr.io/zencart/zencart-test-runner
```

If the test-runner package is public, the workflow can pull it without logging in. If the package is private, add repository
secrets such as `GHCR_TOKEN` and optionally `GHCR_USERNAME`, then log in before running `docker run`.

Example workflow:

```yaml
name: Plugin Tests

on:
  push:
  pull_request:
  workflow_dispatch:

env:
  ZC_CORE_REPOSITORY: zencart/zencart
  ZC_CORE_REF: master
  ZC_PLUGIN_NAME: gdpr-dsar
  ZC_PLUGIN_VERSION: v1.0.2
  ZC_TEST_RUNNER_IMAGE: ghcr.io/zencart/zencart-test-runner

jobs:
  plugin-tests:
    name: PHP ${{ matrix.php-version }} Plugin Tests
    runs-on: ubuntu-latest
    permissions:
      contents: read
      packages: read

    strategy:
      matrix:
        php-version:
          - "8.4"

    services:
      mysql:
        image: mysql:5.7
        env:
          MYSQL_ROOT_PASSWORD: root
          MYSQL_DATABASE: db
          MYSQL_USER: db
          MYSQL_PASSWORD: root
        ports:
          - 3306:3306
        options: >-
          --health-cmd="mysqladmin ping -h 127.0.0.1 -uroot -proot"
          --health-interval=10s
          --health-timeout=5s
          --health-retries=6

    steps:
      - name: Checkout Plugin
        uses: actions/checkout@v4
        with:
          path: plugin

      - name: Checkout Zen Cart
        uses: actions/checkout@v4
        with:
          repository: ${{ env.ZC_CORE_REPOSITORY }}
          ref: ${{ env.ZC_CORE_REF }}
          path: zencart

      - name: Install Plugin Into Zen Cart
        run: |
          mkdir -p "zencart/zc_plugins/${ZC_PLUGIN_NAME}/${ZC_PLUGIN_VERSION}"
          rsync -a --delete \
            --exclude '.git/' \
            --exclude '.github/' \
            plugin/ "zencart/zc_plugins/${ZC_PLUGIN_NAME}/${ZC_PLUGIN_VERSION}/"

      - name: Install Zen Cart Dependencies
        run: |
          docker run --rm \
            --network host \
            -v "${GITHUB_WORKSPACE}/zencart:/var/www/html" \
            -w /var/www/html \
            "${ZC_TEST_RUNNER_IMAGE}:php-${{ matrix.php-version }}" \
            composer install --no-progress --no-interaction --no-ansi --no-scripts

      - name: Patch Vendored Dependencies
        run: |
          docker run --rm \
            --network host \
            -v "${GITHUB_WORKSPACE}/zencart:/var/www/html" \
            -w /var/www/html \
            "${ZC_TEST_RUNNER_IMAGE}:php-${{ matrix.php-version }}" \
            sh -c 'composer update --no-progress --no-interaction --no-ansi --no-scripts && sh not_for_release/testFramework/copyVendorFiles.sh'

      - name: Run Plugin Tests
        run: |
          docker run --rm \
            --network host \
            -v "${GITHUB_WORKSPACE}/zencart:/var/www/html" \
            -w /var/www/html \
            -e ZC_TEST_DB_BASE_NAME=db \
            -e ZC_TEST_DB_WORKERS=2 \
            -e ZC_TEST_DB_INCLUDE_BASE=0 \
            -e ZC_TEST_USE_MAILSERVER=false \
            "${ZC_TEST_RUNNER_IMAGE}:php-${{ matrix.php-version }}" \
            composer tests-plugin -- --plugin "${ZC_PLUGIN_NAME}"

      - name: Upload Test Artifacts
        uses: actions/upload-artifact@v4
        if: always()
        with:
          name: plugin-test-artifacts-php-${{ matrix.php-version }}
          path: zencart/not_for_release/testFramework/logs/console
          if-no-files-found: ignore
          retention-days: 30
```

This example uses `docker run --network host` rather than a job-level `container:` block because the current Zen Cart
runner configuration expects MySQL at `127.0.0.1`. The MySQL service is exposed on the GitHub Actions host at port `3306`,
and the test-runner container can reach it through host networking.

If the test-runner image is private, add this before the first `docker run` step:

```yaml
- name: Login to GHCR
  if: ${{ env.GHCR_TOKEN != '' }}
  env:
    GHCR_TOKEN: ${{ secrets.GHCR_TOKEN }}
    GHCR_USERNAME: ${{ secrets.GHCR_USERNAME }}
  run: |
    echo "${GHCR_TOKEN}" | docker login ghcr.io \
      -u "${GHCR_USERNAME:-${GITHUB_ACTOR}}" \
      --password-stdin
```

For the first workflow, use a single PHP version and one Zen Cart ref. Once that is stable, expand to a matrix:

```yaml
strategy:
  matrix:
    php-version:
      - "8.3"
      - "8.4"
      - "8.5"
    zencart-ref:
      - master
      - v2.1.0
```

Then use the matrix value in the Zen Cart checkout:

```yaml
ref: ${{ matrix.zencart-ref }}
```

Only test against Zen Cart refs that include the `tests-plugin` Composer command and plugin-local test framework support.
Older Zen Cart releases need the test framework backported before this workflow can run against them.

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
Enable `ZC_TEST_USE_MAILSERVER` when a feature or plugin test needs to assert email behavior through an SMTP catcher such
as Mailpit.

Local example:

```bash
ZC_TEST_USE_MAILSERVER=true
ZC_TEST_MAILSERVER_HOST=mailpit
ZC_TEST_MAILSERVER_PORT=1025
ZC_TEST_MAILSERVER_USER=ddev
ZC_TEST_MAILSERVER_PASSWORD=mailpit
```

For container-based plugin CI, pass the same values with `docker run -e ...`. The SMTP host must be reachable from inside
the test-runner container. With `docker run --network host`, a host-level mail catcher is usually reached through
`127.0.0.1`; in Docker Compose or DDEV-style networks it is usually reached by its service name, such as `mailpit`.

Note: Any misconfiguration here will likely result in failing tests.

Yes, you could specify your own real mail server, but beware that when the tests send repeated similar messages they may get falsely treated as spam and may mess with your sender-reputation score.
Mailtrap.io is a developer-friendly tool with a free-tier to accommodate email testing, and is easy to configure.
