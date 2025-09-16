 ---
title: PHP Version Changes and Deprecations
description: Notes about technical changes between PHP versions
category: code
weight: 10
type: codepage
---

PLEASE NOTE THE OFFICIAL PHP VERSION SUPPORT TIMELINE: [https://php.net/supported-versions.php](https://php.net/supported-versions.php)

NOTE: This page assumes some pretty solid PHP knowledge, because all the changes listed will require adapting your code to find a new way to do whatever it was doing before.

NOTE: This is not the complete official list of PHP language changes. This list caters mostly to the topics that might affect people writing plugins for Zen Cart. 
For much more detailed lists of changes, see the [official PHP documentation on migrating between PHP versions](http://www.php.net/manual/en/appendices.php).

## PHP 7

### PHP 7.0
In PHP 7.0 the following functionality/features changed:

a) class `constructors` must be named `__construct` and not just be the same function name as the class anymore.

b) indirection - use of `$$foo['bar']['baz']` needs to be rewritten as `${$foo['bar']['baz']}` else it will be seen as `($$foo)['bar']['baz']`. Also, `$foo->$bar['baz']` has to be rewritten as `$foo->{$bar['baz']}` if that's what was intended.

c) `switch()` statements cannot have multiple `default:` blocks.

Added: Null coalesce operator (`??`) was added: `$username = $_GET['user'] ?? 'guest';` is equivalent to `$username = isset($_GET['user']) ? $_GET['user'] : 'guest';`

Added: spaceship `<=>` comparison operator

Added: `define()` can now define arrays.

Added: `preg_replace_callback_array()`, `random_bytes()`, `random_int()`, `error_clear_last()`

Added: Scalar type declarations and return type declarations.

### PHP 7.1
Zen Cart: ZC sites using PHP 7.0 can safely use 7.1 without issue.

Added: `null`able types (ie: `?` prefix)

Added: `void` return type

Added: array destructuring with `[]`, including in `foreach`

Added: class constants can now declare visibility (protected, private, public)

Added: `is_iterable()` and `iterable` pseudo-type

Deprecated: `mcrypt`


### PHP 7.2
Deprecated: calls to `each()` are deprecated; use `foreach()` instead. 
For upgrading code related to Zen Cart, see some code examples here: [Refactor each() to foreach() for compatibility with PHP 7.2](https://github.com/zencart/zencart/pull/1377)

Deprecated: `create_function()` is deprecated. Use anonymous functions ("Closures") instead.

Deprecated: The `__autoload()` mechanism is deprecated in favor of `spl_autoload_register()` instead.

Deprecated: calls to missing/undefined constants now trigger E_WARNING

Added: Argon2 added to password functions


### PHP 7.3
For PHP 7.3 the only change found necessary in Zen Cart (over PHP 7.2 compatibility) was:
- using the "continue" statement inside a "switch" loop -- should be changed to "break"
- many "strict" conditions now trigger notices

Other notes about 7.3:
- calls to `compact()` with undefined variables will cause errors
- In case of troubleshooting rare problems that could be caused by the very few SPL autoloads in ZC, that any SPL Autoloads that fail will cause all subsequents to fail too, instead of just a warning in previous PHP versions.

Added: `array_key_first()`, `array_key_last()`, `is_countable()`, `hrtime()`, `gc_status()`, `fpm_get_status()`

Added: `DateTime::createFromImmutable()`

Deprecated: case-insensitive constants

### PHP 7.4
Zen Cart note: nested ternary operator calls should be checked for clarity, and extra parentheses added as necessary

Added:  Null coalescing assignment operator: `??=`

Added: Arrow functions, ie: `fn($n) => $n > 0`

Added: [class properties now support type declarations](https://php.watch/versions/7.4/typed-properties) (ie: `int`, `string`, `array` etc)

Added: `password_algos()`, `mb_str_split()`

Added: array unpacking in array literals (`...$arr`)

Added: numeric literal separators (`1_000_000`)

Deprecated: curly-brace array/string offsets. Use `$var[$idx]` instead of `$var{$idx}`

Deprecated: `allow_url_include` INI option

Deprecated: `implode()` MUST specify the separator as the first param (previously the param order could be reversed)

Deprecated: The `is_real()` function is deprecated, use `is_float()` instead.

Deprecated: Using `array_key_exists()` on objects. Instead either `isset()` or `property_exists()` should be used.

Deprecated: The `get_magic_quotes_gpc()` and `get_magic_quotes_runtime()` functions are deprecated. They always return `false`.

Deprecated: `money_format()` replaced by the intl `NumberFormatter` functionality.


### TOOL FOR PHP 5,7 INSPECTION:
Here is a gist containing some [regex patterns which can be used to identify incompatible old PHP code for PHP 5 and PHP 7](https://gist.github.com/drbyte/c188f448137fc149c609)

## PHP 8

### PHP 8.0
Added: `str_contains()`, `str_starts_with()`, `str_ends_with()`

Added: `get_debug_type()`, `preg_last_error_msg()`, `fdiv()`, `DateTimeInterface::createFromInterface()`

Added: constructor property promotion (ie: automatically set $this->var when $var is passed to a typed constructor var)

Added: `match(){};` expression

Added: nullsafe operator (`?->`). ie: `$foo?->value` safely returns `null` if there's no accessible `value` property.

Added: Attributes (#[...])

Added: union types

Deprecated: cannot have function/class parameters with a default value before a required parameter: ie: cannot do: `function foo($required1 = '', $required2)`

### PHP 8.1
Deprecated: can no longer pass `null` to a non-nullable scalar type declaration (ie: `string $var = null` must be either `?string = null` or `string = ''`)

Added: [`enum`](https://www.php.net/manual/en/language.enumerations.php) support

Added: `array_is_list()`

Added: `readonly` properties

Added: first-class callable syntax (`foo(...)`)

Added: intersection types

Added: `never` return type


### PHP 8.2
Added: [`readonly`](https://www.php.net/manual/en/language.oop5.basic.php#language.oop5.basic.class.readonly) classes

Added: constants in traits

Added: `#{\SensitiveParameter]`

Deprecated: dynamic class properties no longer allowed. ie: cannot refer to `$this->foo` if it wasn't previously declared in the class.

Deprecated: The `${var}` and `${expr}` style of string interpolation is deprecated. Use `$var`/`{$var}` and `{${expr}}`, respectively.

Deprecated: `utf8_encode()` and `utf8_decode()` functions are deprecated. (Moved to mbstring extension in PHP 8.4)

Deprecated: `glob()` now returns an empty `array` if all paths are restricted by `open_basedir`. Previously it returned `false`.

### PHP 8.3
Added: `json_validate()` (to validate JSON without decoding first)

Added: `mb_str_pad()`

Added: Typed class constants `const string TEXT_MESSAGE = 'message';`

Change: `number_format()` now handles negative decimals.

### PHP 8.4
Change: `utf8_encode()` and `utf8_decode()` functions are now only present if `mbstring` extension is installed.

Syntax: May now chain `new` expressions, ie: `(new A)->b()->c()`

Deprecated: Implicitly nullable parameters. Must specify `?` or `null` if default is `null`.

Deprecated: E_USER_ERROR, ie: `trigger_error(..., E_USER_ERROR)`

Deprecated: class named `_` no longer allowed.

Added: `request_parse_body()`

Added: `fpow()`

### PHP 8.5
Added functions: `array_first()`, `array_last()`, `get_error_handler()`, `get_exception_handler()`

Added: Pipe operator (`|>`) for enabling functional pipelines.

Added: `final` property promotion

Added: constant expressions may now contain closures and first-class callables.

