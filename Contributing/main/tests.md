1. First, get the composer: go to `getcomposer.org` and do a download,
then follow the Getting Started instructions. 

2. Run `composer install`

3. Add `vendor/bin` to your path.

4. Run all tests, using 
`phpunit -c testFramework/unittests/phpunit.xml`


To add a new test, create your test in an appropriate subdir under testFramework/unittests.

While you are debugging  your test, you may want to just call it in isolation rather than running the entire test suite.
The syntax for doing this is:

`phpunit --filter <test class name> <path to test class file>`

For example,

`phpunit --filter testPaginationCase testFramework/unittests/testsPaginator/paginatorTest.php`

Note that if you have defined constants in your file, you may have to use the trick of setting the class global variables

    protected $preserveGlobalState = FALSE;
    protected $runTestInSeparateProcess = TRUE;

as is done in `testFramework/unittests/testsSundry/AdminFunctionsGeneralTest.php`

If you want to put your tests in a new folder at the level of `testFramework/unittests`, remember to add the new foldername to `phpunit.xml`.
