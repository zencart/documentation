---
title: Test Framework
description: Using the automated tests
weight: 300
layout: docs
---

The Test Framework resides within the `not_for_release/testFramework` directory. This directory is only really available
if you `checkout` the Zen Cart code using git. It is not available if you just download the Zen Cart code via a
`release` link.

Running Zen Cart tests locally has the potential to override your Zen Cart database and destroy data.

FIXME - work in progress

## Preparation / Initial Setup

To prepare to run the Unit Test test suite:

1. First, install Composer:

* go to `getcomposer.org`
* download and install
* follow the Getting Started instructions.

2. Run `composer install`

3. Add `vendor/bin` to your path.

## Unit Tests

Unit tests can be run using

```
composer tests
```

in the root directory of your Zen Cart install.

Currently, there are no local configuration requirements needed to run unit tests.

## Database Integration Tests

Examples of integration tests with a test database are located in
`not_for_release/testFramework/Browser/Dbunit`.

### Database Fixtures

For each database table you need, you must first create a `DatabaseFixture` class under
`not_for_release/testFramework/Support/DatabaseFixtures`. The class must implement:

1. A `createTable()` method with the `CREATE TABLE` sql
2. A `seeder()` method with the `INSERT INTO` sql

See the already present fixtures for the `admin` and the `configuration_group` tables as reference.

At the beginning of the tests the tables will be populated with the seed data, and then truncated at the end of the
tests (using Laravel Capsule).

### Configuration file

Create a configuration file under `not_for_release/testFramework/Support/DatabaseConfigure`
using `runner.configure.dusk.php` as template. The file must be named `<user>.configure.dusk.php`, where `<user>` is
replaced by the user that your php scripts run as (usually equal to `$_SERVER['USER']`). The file must contain the 
test database information (address, user, password, etc.)

### Test case

The class `not_for_release/testFramework/Browser/Dbunit/DatabaseTest.php` is an example of how the test case should be
structured:

```
use App\Models\Admin;
use Tests\Support\Traits\DatabaseConcerns;
use Tests\Support\zcUnitTestCase;

class DatabaseTest extends zcUnitTestCase
{
    use DatabaseConcerns;

    public $databaseFixtures = ['adminEmpty' => ['admin'], 'configurationGroup' => ['configuration_group']];

    public function testExample()
    {
        $f = Admin::all();
        $this->assertTrue(!count($f));
        $f = $this->db->Execute('SELECT * FROM ' . TABLE_ADMIN);
        $this->assertTrue(!$f->count());
    }
}
```

The trait `DatabaseConcerns` takes care of setting up the test database. `$databaseFixtures` is the list of Database
Fixtures used by the tests.

You can also optionally use the Eloquent syntax by importing the database models first, located under
`laravel/App/Models`.

Run the test case with `phpunit` like so:

```
phpunit --verbose --testsuite <TestSuite> --printer 'Sempro\PHPUnitPrettyPrinter\PrettyPrinterForPhpUnit9'
```

In the example above, `<TestSuite>` is `Dbunit`.

## Browser Tests

**NOTE:** these tests have been temporarily removed from the repo, so the instructions below are no more valid right
now.
They are still a useful reference, and you can find the files in the repo history on github.

Automated browser tests can be run using

```
composer dusk
```

in the root directory of your Zen Cart install.

There are configuration requirements needed to run browser tests on your local machine.

### Browser Test Configuration

If you want to run browser tests on your local machine, you will need to create 3 configuration files.

`<user>` is replaced by the user that your php scripts run as. You can find this by echoing `$_SERVER['USER']` in
some php script.

1. In `not_for_release/testFramework/Browser/duskConfigures` you will need to create a file called `<user>.configure.dusk.php`.
    An example file `dusk.configure.php` can be used as a template. Note: The database user 
   `TESTING_DB_SERVER_USERNAME` must have sufficient rights to create a database.

2. `not_for_release/testFramework/Browser/zencartConfigures/admin.<user>.configure.php`

3. `not_for_release/testFramework/Browser/zencartConfigures/catalog.<user>.configure.php`

Files 2. and 3. should be copies of the normal `configure.php` files that you would have in
`admin/includes/configure.php` and `includes/configure.php`.

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
