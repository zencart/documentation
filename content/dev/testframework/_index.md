---
title: Test Framework
description: Using the automated tests
weight: 300
layout: docs
---

The Test Framework resides within the `not_for_release/testFramework` directory. This directory is only really available
if you `checkout` the Zen Cart code using `git`. It is not available if you just download the Zen Cart code via a
`release` link.

ALERT: Running Zen Cart tests locally has the potential to **overwrite your Zen Cart database and destroy data.**

FIXME - work in progress

## Preparation / Initial Setup

To prepare to run the Unit Test and Feature Test suites:

1. First, install Composer on your PC:

* go to `getcomposer.org`
* download and install according to your operating system
* follow the Getting Started instructions.

2. Run `composer install` from inside root directory of your Zen Cart, on your PC.

## Unit Tests

Unit tests can be run using:

```
composer unit-tests
```

in the root directory of your Zen Cart install.

Currently there are no local configuration requirements needed to run unit tests.

## Feature Tests

While unit tests allow testing of functions/classes and other small fragments of code, feature tests allow 
testing of the application as a whole. The tests will typically access the application via URLs and test the resulting html returned by those URLs.
Feature tests can also interact with the application, by setting form values and submitting those forms.

NOTE: Current feature tests don't support javascript so interactions with pages that use javascript may not be possible.
It is planned in the future to allow interactions with pages that rely on javascript using something like `Selenium` or `Panther`.

WARNING: Feature tests rely on Re-creating the database on each separate test suite. This means it will destroy you database. 
However, given that you should only be testing on a local development environment, this shouldn't be a problem.

Feature tests can be run using `composer functional-tests`

### Configuration

Feature tests override the standard `configure.php` files used by Zen Cart and require you to create new configure files just for testing purposes.

Your configure files should be created in the `not_for_release/testFramework/Support/configs` directory and will be named 

`_USER_.store.configure.php` and `_USER_.admin.configure.php` where the `_USER_` is replaced by the user that your local environment runs as.

You can find that user by running the following from the root of your installation.

`php ./not_for_release/testFramework/detectUser.php`

These files are exactly the same format as standard Zen Cart `configure.php` files and you can copy the 
`admin.configure.php.example` and `store.configure.php.example` files as starting points.

### Migrations and Seeders

As the functional tests rely on a populated database, the test framework uses Laravel-like migrations and seeders.

Migrations create the tables we need and seeders add data to the tables. 

The initial migrations and seeders are run automatically by the test framework and mirror what 
would be created by zc_install with demo data.

There may be times though where you may want to alter the data to test a specific bug. 
An example may be when a search is not finding a product that contains certain strings, 
or a salemaker with specific data is not applying correctly.

In these cases you can create your own data seeder to add this data just for your test.

Custom seeders are created in the `not_for_release/testFramework/Support/database/Seeders/CustomSeeders/` directory.

An example is `not_for_release/testFramework/Support/database/Seeders/CustomSeeders/StoreWizardSeeder.php`

You can run a custom seeder in your tests using 

`$this->runCustomSeeder('StoreWizardSeeder');`

replacing `StoreWizardSeeder` with the name of your seeder class.

