---
title: Testing
weight: 6
---
# Unit Testing
Writing automated tests is important to ensure that the tested features function properly both before and after making future changes to the system.


# Preparation / Initial Setup
To prepare to run the Unit Test test suite:

1. First, install Composer: 
 * go to `getcomposer.org`
 * download and install 
 * follow the Getting Started instructions. 

2. Run `composer install`

3. Add `vendor/bin` to your path.


## Running Tests

Run all tests, using:

`phpunit -c testFramework/unittests/phpunit.xml`


### Running Individual Tests

While you are debugging a specific test (such as one you're adding, see below), you may want to just call it in isolation rather than running the entire test suite.
The syntax for doing this is:

`phpunit --filter <test class name> <path to test class file>`

For example,

`phpunit --filter testPaginationCase testFramework/unittests/testsPaginator/paginatorTest.php`


## Adding Tests
To add a new test, create your test in an appropriate subdir under `testFramework/unittests`.

### Test Tips
* Note that if you have defined constants in your file, you may have to use the trick of setting the class global variables as is done in `testFramework/unittests/testsSundry/AdminLoggingTest.php`:

```
    protected $preserveGlobalState = FALSE;
    protected $runTestInSeparateProcess = TRUE;
```

* If you want to put your tests in a new folder at the level of `testFramework/unittests`, remember to add the new foldername to `phpunit.xml`.



--------------------------------------


# Web Tests
Some features can only be properly tested by running them through a browser. We do this using Selenium and Firefox.

## Preparation and Setup for Web Tests
1. Follow the Prep/Setup above for Unit Testing, as these are dependencies for the Web Tests
2. [Install a Java JDK](http://www.oracle.com/technetwork/java/javase/downloads/index.html) if one isn't already on your computer
3. Download [Selenium Server Standalone](http://docs.seleniumhq.org/download/) Java Agent. This will give you a `selenium-server-standalone-<version>.jar` file.
4. Install [Firefox](http://getfirefox.com) if not already present. 

>Be aware that sometimes the "latest" Firefox may not work with Selenium ... so occasionally may need to use an older Firefox version, or upgrade Selenium to a newer version.


## Preparing custom configurations
WebTests need to run from a local webserver, so you need a MySQL+Apache/Nginx (or equivalent) setup already present on your computer, and need to be able to access it from your installed Firefox browser. The Zen Cart Habitat server is ideal for this.

Since the webtests will run zc_install, be prepared for your database to be wiped out and your configure.php files to be updated.

In the `testFramework/config/` folder there is a `localconfig_EXAMPLE.php` file. Make a copy of that file and configure it to suit your local environment:

 1. filename: `localconfig_YOURUSERNAME.php` ... ie: if I login to my PC as `bill` then the filename would be: `localconfig_bill.php`
 
 2. Inside the file, edit the `define` statements to reflect your local webserver's domain name, database credentials, etc for your Zen Cart dev site.  If you're running in a Zen Cart Habitat environment, the `WEBTEST_ADMIN_PASSWORD_INSTALL` should be set to `developer1`.


## Running Web Tests
a) Start Selenium engine from command line:

    java -jar <path_to>/selenium-server-standalone-<version>.jar -trustAllSSLCertificates

b) Start the webtests in another terminal window:

	phpunit -c testFramework/webtests/phpunit.xml

