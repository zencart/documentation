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

While you are debugging a specific test (such as one you're adding, see below), you may want to just call it in isolation rather than running the entire test suite.
The syntax for doing this is:

`phpunit --filter <test class name> <path to test class file>`

For example,

`phpunit --filter testPaginationCase testFramework/unittests/testsPaginator/paginatorTest.php`


## Adding Tests
To add a new test, create your test in an appropriate subdir under `testFramework/unittests`.

Note that if you have defined constants in your file, you may have to use the trick of setting the class global variables

```
    protected $preserveGlobalState = FALSE;
    protected $runTestInSeparateProcess = TRUE;
```

as is done in `testFramework/unittests/testsSundry/AdminLoggingTest.php`

If you want to put your tests in a new folder at the level of `testFramework/unittests`, remember to add the new foldername to `phpunit.xml`.



--------------------------------------


# Web Tests
Some features can only be properly tested by running them through a browser.

We do this using Selenium and Firefox.

## Preparation and Setup for Web Tests
1. Follow the Prep/Setup above for Unit Testing, as these are dependencies for the Web Tests
2. [Install a Java JDK](http://www.oracle.com/technetwork/java/javase/downloads/index.html) if one isn't already on your computer
3. Download [Selenium Server Standalone](http://docs.seleniumhq.org/download/) Java Agent
4. Install [Firefox](http://getfirefox.com) if not already present
5. OPTIONAL: create a separate clean "profile" in Firefox, and tell Selenium to use this profile to be used in your tests

## Running Web Tests
a) Start Selenium engine from command line:

    java -jar <path_to>/selenium-server-standalone-<version>.jar

or, to also specify a custom Firefox user profile, use:

	java -jar <path_to>/selenium-server-standalone-<version>.jar -firefoxProfileTemplate "<path_to>/Firefox/Profiles/<profile_name_here>" &

b) Start the webtests:

	phpunit -c testFramework/webtests/phpunit.xml


