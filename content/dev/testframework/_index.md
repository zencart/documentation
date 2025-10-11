---
title: Test Framework
description: Using the automated tests
weight: 300
layout: docs
---

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


