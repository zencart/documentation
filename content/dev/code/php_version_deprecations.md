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

d) Null coalesce operator (`??`) was added: `$username = $_GET['user'] ?? 'guest';` is equivalent to `$username = isset($_GET['user']) ? $_GET['user'] : 'guest';`

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


### PHP 8.0
Functions added: `str_contains()`, `str_starts_with()`, `str_ends_with()`; `get_debug_type()`, `preg_last_error_msg()`, `fdiv()`, `DateTimeInterface::createFromInterface()`

Added: Named arguments, attributes (#[...])

Added: constructor property promotion (ie: automatically set $this->var when $var is passed to a typed constructor var)

Added: union types, `match` expression, nullsafe operator (`?->`)

Deprecated: cannot have function/class parameters with a default before a required parameter.

### PHP 8.1
Added: `array_is_list()`

Added: [`enum`](https://www.php.net/manual/en/language.enumerations.php) support

Added: `readonly` properties

Added: first-class callable syntax (`foo(...)`)

Added: intersection types

Added: `never` return type

Deprecated: can no longer pass `null` to a non-nullable scalar type declaration (ie: `string $var = null` must be either `?string = null` or `string = ''`)

### PHP 8.2
Added: [`readonly`](https://www.php.net/manual/en/language.oop5.basic.php#language.oop5.basic.class.readonly) classes

Added: constants in traits

Added: `#{\SensitiveParameter]`

Deprecated: dynamic class properties no longer allowed. ie: cannot refer to `$this->foo` if it wasn't previously declared in the class.

Deprecated: The `${var}` and `${expr}` style of string interpolation is deprecated. Use `$var`/`{$var}` and `{${expr}}`, respectively.

Deprecated: `glob()` now returns an empty `array` if all paths are restricted by `open_basedir`. Previously it returned `false`.

Deprecated: `utf8_encode()` and `utf8_decode()` functions are deprecated. (Moved to mbstring extension in PHP 8.4)

### PHP 8.3
Added: `json_validate()` (to validate JSON without decoding first)

Added: `mb_str_pad()`

Added: Typed class constants

`number_format()` now handles negative decimals.

### PHP 8.4
Added: `request_parse_body()`

Added: `fpow()`

Change: `utf8_encode()` and `utf8_decode()` functions are now only present if `mbstring` is installed.

Syntax: May now chain `new` expressions, ie: `(new A)->b()->c()`

Deprecated: Implicitly nullable parameters. Must specify `?` or `null` if default is `null`.

Deprecated: E_USER_ERROR, ie: `trigger_error(..., E_USER_ERROR)`

Deprecated: class named `_` no longer allowed.

### PHP 8.5
Added: Pipe operator (`|>`) for enabling functional pipelines.

Added: `final` property promotion

Added functions: `array_first()`, `array_last()`, `get_error_handler()`, `get_exception_handler()`

Added: constant expressions may now contain closures and first-class callables.

