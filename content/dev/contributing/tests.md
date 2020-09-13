---
title: Testing
description: Using the automated tests 
weight: 6
---

# Preparation / Initial Setup
To prepare to run the Unit Test test suite:

1. First, install Composer: 
 * go to `getcomposer.org`
 * download and install 
 * follow the Getting Started instructions. 

2. Run `composer install`

3. Add `vendor/bin` to your path.

The test framework exists in the `not_for_release/testFramework` directory.

# Running Tests

## Unit Tests 

Unit tests can be run using 

`composer tests`

in the root directory of your Zen Cart install.

Currently, there are no local configuration requirements needed to run unit tests. 

## Browser Tests

Automated browser tests can be run using 

`composer dusk`

in the root directory of your Zen Cart install.

There are configuration requirements needed to run browser tests on your local machine.

### Browser Test Configuration

If you want to run browser tests on your local machine, you will need to create 3 configuration files.

In `not_for_release/testFramework/Browser/duskConfigures` you will need to create a file called

`$user.configure.dusk/php` where `$user` is replaced by the user that your php scripts run as.

You can find this by echoing $_SERVER['USER] in some php script.

An example file `dusk.configure.php` can be used as a template.

Note: The database user `TESTING_DB_SERVER_USERNAME` must have sufficient rights to create a database.

The other configuration files needs to be created in 
`not_for_release/testFramework/Browser/zencartConfigures`and be named 

`admin.$user.configure.php` and `catalog.$user.configure.php` again with `$user` replaced with the user the php 
scripts run as.

These configure files should be copies of the normal `configure.php` files that you would have in 
`admin/includes/configure.php` and `includes/configure.php`

### Admin Alert Page

Normally, if the zc_install directory exists Zen Cart will display an alert page on any attempt to access
admin URI's. FIXME

### Database Regeneration

When Browser tests are run, and in order to create some isolation between various tests the framework will 
dump whatever database you have set in the configuration files mentioned earlier.

It will then load the default database schema from `zc_install/sql/install/mysql_zencart.sql` and the demo 
data from `zc_install/sql/demo/mysql_demo.sql` 

This means that if your testing database contains any changes from the default install, they will be lost.

If your need to keep your local changes then you must ensure that they have been added to 
`zc_install/sql/install/mysql_zencart.sql` and `zc_install/sql/demo/mysql_demo.sql` before running 
the browser tests.
 
FIXME
