Introduction to v2
==================

Zen Cart v2 represents a major shift from previous versions. We are introducing a lot of new re-written code,
which is meant to make life easier for those developing with/for Zen Cart, and to make plugin code easier to install. 

To help developers we are also creating lots of new documentation resources for that code.

## Getting Composer 
If you don't yet have composer installed, do this first: 
 * go to `getcomposer.org`
 * download and install 
 * follow the Getting Started instructions. 

## Generating code-level documentation (php-documentor)

Assuming you have a complete checkout of Zen Cart on your local machine, and have run `composer install` to set it up for development work, you can generate the php-doc documentation by running the following from the root of the repository:

```sh
phpdoc
``` 

If you get errors that it won't/can't run, be sure to run:

```sh
composer install
```
or even
```sh
composer update
```
to set up the dependencies.


## Unit Testing

To run unit tests with phpunit, you must have `composer` set up, similar to above, and then you can run the following from the root of the repository directory:

```sh
phpunit -c testFramework/unittests/phpunit.xml
```

