 ---
title: PHP Version Changes and Deprecations
description: Notes about technical changes between PHP versions
category: code
weight: 10
type: codepage
---

# PHP Version Changes and Deprecations

PLEASE NOTE THE OFFICIAL PHP VERSION SUPPORT TIMELINE: [https://php.net/supported-versions.php](https://php.net/supported-versions.php)

NOTE: This post assumes some pretty solid PHP knowledge, because all the changes listed will require adapting your code to find a new way to do whatever it was doing before.

NOTE: This is not the complete official list of changes. This list caters mostly to the topics that might affect people writing plugins for Zen Cart. 
For much more detailed lists of changes, see the [official PHP documentation on migrating between PHP versions](http://www.php.net/manual/en/appendices.php).

## PHP 7

### PHP 7.0
In PHP 7.0 the following functionality/features changed:

a) class `constructors` must be called `__construct` and not just be the same function name as the class anymore.

b) indirection - use of `$$foo['bar']['baz']` needs to be rewritten as `${$foo['bar']['baz']}` else it will be seen as `($$foo)['bar']['baz']`. Also, `$foo->$bar['baz']` has to be rewritten as `$foo->{$bar['baz']}` if that's what was intended.

c) `switch()` statements cannot have multiple `default:` blocks.

### PHP 7.1
In PHP 7.1 there were numerous changes, but few likely to impact regular Zen Cart use

PHP 7.1 is nearly identical to PHP 7.0 in terms of compatibility, but 7.1 is faster, so there's no point in using 7.0 if 7.1 is available to you!


### PHP 7.2
For PHP 7.2 the following changes are required:

a) calls to `each()` are deprecated; use `foreach()` instead. See examples here: [Refactor each() to foreach() for compatibility with PHP 7.2](https://github.com/zencart/zencart/pull/1377)

b) `create_function()` is deprecated. Use anonymous functions ("Closures") instead.

c) The `__autoload()` mechanism is deprecated in favor of `spl_autoload_register()` instead.

### PHP 7.3
For PHP 7.3 the only change found necessary in Zen Cart (over PHP 7.2 compatibility) was:
- using the "continue" statement inside a "switch" loop -- should be changed to "break"
- many "strict" conditions now trigger notices

Other notes about 7.3:
- calls to `compact()` with undefined variables will cause errors
- In case of troubleshooting rare problems that could be caused by the very few SPL autoloads in ZC, that any SPL Autoloads that fail will cause all subsequents to fail too, instead of just a warning in previous PHP versions.

### PHP 7.4
- nested ternary operator calls should be checked for clarity, and extra parentheses added as necessary
- added Null coalescing assignment operator: `??=`


Here is a gist containing some [regex patterns which can be used to identify incompatible old PHP code for PHP 5 and PHP 7](https://gist.github.com/drbyte/c188f448137fc149c609)


