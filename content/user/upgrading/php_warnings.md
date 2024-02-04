---
title: PHP Errors, Warnings and Deprecated messages after upgrading
description: How to fix the most common PHP7+ messages
category: upgrading 
weight: 10
---

As you upgrade PHP from an older version, these are [debug log messages](/user/troubleshooting/debug_logs/) you will commonly see.  An explanation of *why this can happen* is provided in [understanding errors after upgrading PHP versions](/user/troubleshooting/php_debug_logs). This article explains *how to fix* some of the most common problems you will see. 

There are several levels of PHP problems, with the least serious being _notices_ and _warnings_. 

More serious are PHP _errors_, which can cause a blank screen or partially blank screen.  If you are experiencing errors, you should also read the [blank pages troubleshooting guide](/user/troubleshooting/blank_page/).

Please take these as examples, not exact matches for every log you might come across. 

## Logs related to PHP8 

PHP8 is a *major change*.  Zen Cart 1.5.8 is designed to work with PHP 8, but older versions and older plugins will give you problems.  Here are some notes on [updating plugins to work with PHP8](/dev/plugins/upgrading_to_158/).

If you are using PHP 8.0 with v1.5.7, be sure to [suppress logging duplicate-language definitions](/user/troubleshooting/constant_already_defined/).

### Logs related to PHP 8.2

PHP 8.2 is *the deprecation release*.  We have tried to shake out as many of the issues in the core as we could prior to release, but there may be some lingering, and there will absolutely be issues with plugins.  See [upgrading plugins to work with 1.5.8/PHP 8.0+](/dev/plugins/upgrading_to_158/) for ideas on how to fix the issues you encounter.  You may also wish to [track development of Zen Cart on Github](https://github.com/zencart/zencart/) to see what we're preparing for the next release.

## Undefined constant 

```
--> PHP Warning: Use of undefined constant MODULE_SHIPPING_BOXES_MANAGER_STATUS - assumed 'MODULE_SHIPPING_BOXES_MANAGER_STATUS' (this will throw an Error in a future version of PHP) in /public_html/zen-cart-v1.5.7/includes/modules/shipping/fedexwebservices.php on line 85.
```

When you get a message like this, it means you are referencing a constant that hasn't been defined.  You can work around this by defining the constant or just by putting a check in where the constant is referenced.  The latter would be done as follows: 

Change 

```
    if (MODULE_SHIPPING_BOXES_MANAGER_STATUS == 'true') {
```

to 

```
    if (defined('MODULE_SHIPPING_BOXES_MANAGER_STATUS') && MODULE_SHIPPING_BOXES_MANAGER_STATUS == 'true') {
```

Another variant of the undefined constant problem can occur in language files. 

```
--> PHP Warning: Use of undefined constant BUTTON_IMAGE_ADD_TO_CART - assumed 'BUTTON_IMAGE_ADD_TO_CART' (this will throw an Error in a future version of PHP) in /public_html/zen-cart-v1.5.7/includes/modules/YOURTEMPLATE/specials_index.php on line 86.
```

In this case, your template is using a defined constant which does not exist in your language file set.  If the define is used in multiple places, you can add it to `includes/languages/YOURTEMPLATE/english.php` or another globally loaded file; otherwise, add it to the language file for the page in question. 

In this case, we'll add this statement to the file `includes/languages/english/YOURTEMPLATE/button_names.php`, which is loaded for all pages. 

```
define('BUTTON_IMAGE_ADD_TO_CART', 'button_add_to_cart.gif');
```


## Methods with the same name as their class ...  

```
--> PHP Deprecated: Methods with the same name as their class will not be constructors in a future version of PHP; fedexwebservices has a deprecated constructor in /public_html/zen-cart-v1.5.7/includes/modules/shipping/fedexwebservices.php on line 2.
```

To fix this, change the class constructor from being the same as the name of the class like this:

```
class fedexwebservices 
{
    function fedexwebservices() 
    ...
}
```

to this:

```
class fedexwebservices 
{
    function __construct() 
    ...
}
```

## Cannot use string offset as an array

In older versions of PHP, it was acceptable to initialize a variable as an empty string even though it was later being accessed as an array. So in some older code you might have something like this:

```
$list_box_contents = ''; 
```

where newer versions require the correct initialization as:

```
$list_box_contents = array();
```

(or you may see the more modern "short array syntax" like this):

```
$list_box_contents = [];
```


## `each()` deprecated

```
PHP Deprecated: The each() function is deprecated. This message will be suppressed on further calls in /includes/functions/extra_functions/sfl_functions.php on line 160.
```

The direction for PHP 7.2+ is to refactor `each` to `foreach` as follows: 

1. `foreach()` doesn't need a `reset()` to be called before it runs, so those can be removed.

2. There are 3 syntax formats, depending on how the parameters are presented in the `list()` call:

    a) `while(list($key, $value) = each($foo))`
    This becomes `foreach($foo as $key => $value)`

    b) `while(list(, $value) = each($foo))`
    This becomes `foreach($foo as $value)`

    c) `while(list($key, ) = each($foo))`
    This becomes `foreach($foo as $key => $value)`



## `ereg_replace` deprecated

Some older functions were removed from PHP. The `ereg` series can usually be replaced with a `preg` equivalent, but note that the "pattern" parameter needs to have a delimiter added. In many cases a `/` or `~` is used for the delimiter ... this must be adapted to your situation.

`ereg('searchtext', 'a_string', $optionalVar)` becomes `preg_match('/searchtext/', 'a_string', $optionalVar)`

`eregi('searchtext', 'a_string', $optionalVar)` becomes `preg_match('/searchtext/i', 'a_string', $optionalVar)`

`ereg_replace('searchtext',.....)` becomes `preg_replace('/searchtext/',....)`

  ... or if the `'searchtext'` parameter is just a single character then just change `ereg_replace` with `str_replace`

`eregi_replace('searchtext',.....)` becomes `preg_replace('/searchtext/i',....)`


`split('x', $var)` has a couple options:
- if 'x' is a single character, then `split(` becomes `explode(`
- if 'x' is multiple characters, then `split('chars', $var)` becomes `preg_split('/chars/', $var)`


## syntax error, unexpected '['


This may be a result of new indirection syntax (or "variable variables" syntax), where double-dollar-signs are used.

This situation is sometimes found in old not-yet upgraded payment modules where additional braces `{`, `}` must be added. For example:

Replace this:
```
global $$order_totals[$i]['code'];
```

with

```
global ${$order_totals[$i]['code']};
```

And

```diff
if ($$order_totals[$i]['code']->credit_class == true) $credits_applied += $order_totals[$i]['value'];
```

with

```
if (${$order_totals[$i]['code']}->credit_class == true) $credits_applied += $order_totals[$i]['value'];
```


On a technical note, what's required is the addition of braces for adding the necessary specificity. More generic examples include the following:

Use of `$$foo['bar']['baz']` needs to be rewritten with braces around the whole of it, like `${$foo['bar']['baz']}` else it will be treated incorrectly as `($$foo)['bar']['baz']`. 

Also when referring to an object, `$foo->$bar['baz']` has to be rewritten as `$foo->{$bar['baz']}` if that's what was intended in the older code.



## Unknown function `mysql(`

Since PHP 5.5 the `mysql_xxxxx()` functions were removed in favor of the `mysqli_xxxxx()` function series.

You cannot just rename the functions. 

While on the surface it may seem simple to rewrite the functions to the new syntax, a MUCH BETTER approach is to rewrite your code to use Zen Cart's own DB querying logic, which is both more secure and more consistent across the application.

## Undefined constant warnings in module files

Files under `/includes/modules/payment`, `/includes/modules/shipping` and `/includes/modules/order_total` were updated in Zen Cart 1.5.6 so that module defines were not referenced until it was determined that the module had been installed.  

Using the example of `shipping/flat.php`, prior to 1.5.6, the constructor would do

```
      $this->sort_order = MODULE_SHIPPING_FLAT_SORT_ORDER;
```

This will generate a warning in newer versions of PHP if `flat` is not installed, since the variable `MODULE_SHIPPING_FLAT_SORT_ORDER` will not be in the database. 

Newer versions of Zen Cart check the sort order as an indication that a module has been installed, and return early if it is not defined.

```
      $this->sort_order = defined('MODULE_SHIPPING_FLAT_SORT_ORDER') ? MODULE_SHIPPING_FLAT_SORT_ORDER : null;
      if (null === $this->sort_order) return false;
``` 

If you have custom modules, you should make the analagous change to those files to avoid creating PHP warnings. 

## Sizeof and related issues

Older PHP code might check to see if a string is null using something like: 

```
    if (sizeof($categories->fields['categories_image']) == 0) 
```

The newer way to test this is to use the `empty` PHP function: 


```
    if (empty($categories->fields['categories_image'])) 
```

Similarly, checks for a non-empty array may need changes: 

```
    if (sizeof($array) > 0) {
```

Could give a PHP warning like:

```
Warning: sizeof(): Parameter must be an array or an object that implements Countable
```

To avoid this, check the value using `empty` 

```
    if (!empty($array)) {
```

When specific array entries don't exist in some cases, for example if 

```
    $this->ccv_response= $response[38];
```
 
produces the error message 

```
--> PHP Warning: Undefined array key 38 
```

You can use an empty check to handle this, as shown above, or you can use the null coalescing operator:  

```
    $this->ccv_response= ($response[38] ?? '');
```

## Undefined array key

Checking to see if an optional array element is set has changed - you can no longer do 

```
if ($response['var1'] != '') {
```
unless you are certain the array element `var1` exists. 

If you do this, and the element does not exist, you will get a PHP Warning

```
--> PHP Warning: Undefined array key var1 
```


If the array element is referenced in the middle of a statement, use the [null coalescing operator](/dev/code/php_idioms/#null-coalescing-operator) to prevent invalid references. 

So for example, if `$response['var1']` might not be set, change 

```
echo 'Message is ' . $response['txt'] . ' ' . $response['var1']; 
``` 

to 

```
echo 'Message is ' . $response['txt'] . ' ' . ($response['var1'] ?? ''); 
``` 

Similarly, if the array element is referenced on the right hand side of an equals sign, you can use the null coalescing operator.

If you get 

```
--> PHP Notice: Undefined index: order_add_comment 
```

from 

```
$order->info['comments'] = $_SESSION['order_add_comment'];
```

change to

```
$order->info['comments'] = ($_SESSION['order_add_comment'] ?? '');
```

## Array and string offset access syntax with curly braces is no longer supported

In older versions of PHP, you could refer to an array entry using curly braces instead of square brackets. 

PHP 7.4 deprecated this syntax, and in higher versions of PHP it becomes a fatal error.  Fortunately, This is one of the easiest syntax errors to fix. Simply change the curly braces to square brackets.  So for example, change 

```
        $c = $s{$i};
```

to 

```
        $c = $s[$i];
```

<hr>

{{% code_help_links %}} 
