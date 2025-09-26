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

## Zen Cart code compatibility notes
Refer to the [Zen Cart PHP version compatibility matrix](/user/first_steps/server_requirements/#php-version)

#### The following PHP changes required core ZC code changes for compatibility _when upgrading from prior versions_:
- PHP 7.0 requires classes to use `__construct` as the function name instead of just using the name of the class as a constructor.
- PHP 7.2 deprecated the `each()` function, which was used prolifically before then.
- PHP 7.4 requires implode/explode to provide the separator as first arg.
- PHP 8.0 requires that any optional function params come after non-optional.
- PHP 8.2 requires class properties (`$this->var's`) to be declared before referring to them in class code.
- PHP 8.4 requires that nullable parameters be declared as such in function signatures.
- PHP 8.4 Deprecated `E_USER_ERROR` ie: `trigger_error(..., E_USER_ERROR)`

See related upgrade docs for [mitigation guidance](/user/upgrading/php_warnings/) on these topics.

#### The following PHP changes are important to note when _backporting code to older ZC versions_:
- To add support for most **PHP functions added to the PHP language since PHP 7.0**, use the [php_polyfill.php](https://github.com/zencart/zencart/blob/master/includes/functions/php_polyfills.php) (in v1.5.7c or newer, replace it in /includes/functions. In v1.5.7b or older, put it into your `extra_configures` folders in *both* *admin and non-admin*)
 
However, the polyfill only deals with missing functions. The following language constructs, if you're using them, will require changing your syntax to older-style PHP approaches, in order to work on older PHP versions:
- PHP 7.0 added null coalesce (`??`) operator
- PHP 7.0 added function/class `return types`
- PHP 7.0 added the spaceship `<=>` operator
- PHP 7.0 added `yield from` syntax
- PHP 7.0 added `Throwable`
- PHP 7.0 added `declare strict_types` syntax
- PHP 7.1 added `nullable types`, ie: `?string`, `?int`, `?array`
- PHP 7.4 added null coalesce assignment `??=`
- PHP 7.4 added arrow functions `fn($n) => $n > 0`
- PHP 8.0 added `match` syntax
- PHP 8.0 added `#[...]` Attributes

More details on all of these can be found in the rest of this document, and on the PHP.net website.

---

# PHP Language History (abbreviated summary)

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

Added: [Scalar type declarations and return type declarations](https://www.php.net/manual/en/migration70.new-features.php): string, int, float, bool, array, callable, class names and interfaces.

Removed: The POSIX "ereg" family of functions was fully removed: `ereg(), eregi(), ereg_replace(), eregi_replace(), split(), spliti()`. See [mitigation](/user/upgrading/php_warnings/#ereg_replace-deprecated)

### PHP 7.1
Zen Cart: ZC sites using PHP 7.0 can safely jump to PHP 7.1 without issue.

Added: `null`able types (ie: `?` prefix)

Added: `void` return type

Added: [array destructuring](https://stitcher.io/blog/array-destructuring-with-list-in-php) with `[]`, including in `foreach`

Added: class constants can now declare visibility (protected, private, public)

Added: `is_iterable()` and `iterable` pseudo-type

Deprecated: `mcrypt`


### PHP 7.2
Deprecated: calls to `each()` are deprecated; [use `foreach()` instead](/user/upgrading/php_warnings/#each-deprecated).
For upgrading code related to Zen Cart, see some code examples here: [Refactor each() to foreach() for compatibility with PHP 7.2](https://github.com/zencart/zencart/pull/1377)

Deprecated: `create_function()` is deprecated. Use anonymous functions ("Closures") instead.

Deprecated: The `__autoload()` mechanism is deprecated in favor of `spl_autoload_register()` instead.

Deprecated: calls to missing/undefined constants now trigger `E_WARNING: Warning: Use of undefined constant FOO – assumed 'FOO'.` (Now a fatal error since PHP 8.0)

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

Added: Attributes (`#[...]`)

Added: union types (`(int|string)` which is "or" matching, eg: `int|string` means could be an int or a string)

Deprecated: cannot have function/class parameters with a default value before a required parameter: ie: cannot do: `function foo($required1 = '', $required2)`

Deprecated: calls to undefined constants now throw `Fatal error: Uncaught Error: Undefined constant "FOO"`


### PHP 8.1
Deprecated: can no longer pass `null` to a non-nullable scalar type declaration (ie: `string $var = null` must be either `?string = null` or `string = ''`)

Added: [`enum`](https://www.php.net/manual/en/language.enumerations.php) support

Added: `array_is_list()`

Added: `readonly` properties

Added: first-class callable syntax (`foo(...)`)

Added: intersection types (`A&B` where A and B are interfaces, both of which must be implemented)

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

Added: [Typed class constants](https://php.watch/versions/8.3/typed-constants) `const string TEXT_MESSAGE = 'message';`

Change: `number_format()` now handles negative decimals.

### PHP 8.4
Added: New `mb_trim`, `mb_ltrim`, and `mb_rtrim` functions

Change: `utf8_encode()` and `utf8_decode()` functions are now only present if `mbstring` extension is installed.

Syntax: May now chain `new` expressions, ie: `(new A)->b()->c()`

Deprecated: Implicitly nullable parameters. Must specify `?` or `null` if default is `null`.

Deprecated: E_USER_ERROR, ie: `trigger_error(..., E_USER_ERROR)`

Deprecated: classes named `_` no longer allowed.

Deprecated: `E_STRICT` constant deprecated

Added: `request_parse_body()`

Added: `fpow()`

### PHP 8.5
Added functions: `array_first()`, `array_last()`, `get_error_handler()`, `get_exception_handler()`

Added: [Pipe operator](https://php.watch/versions/8.5/pipe-operator) (`|>`) for enabling functional pipelines.

Added: `final` property promotion

Added: constant expressions may now contain closures and first-class callables.

Deprecated: [Non-canonical scalar type casts (boolean|double|integer|binary)](https://php.watch/versions/8.5/boolean-double-integer-binary-casts-deprecated)

