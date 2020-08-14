---
title: PHP Warnings and Deprecated messages after upgrading
description: How to fix the most common PHP7 messages
category: upgrading 
weight: 10
---

As you upgrade PHP from an older version, these are log messages you will commonly see.  They are very easy to fix.  Please take these as examples, not exact matches for every log you might come across. 

### Undefined constant 

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

### Methods with the same name as their class ...  

```
--> PHP Deprecated: Methods with the same name as their class will not be constructors in a future version of PHP; fedexwebservices has a deprecated constructor in /public_html/zen-cart-v1.5.7/includes/modules/shipping/fedexwebservices.php on line 2.
```

To fix this, change the class constructor from 

```
function fedexwebservices() 
```

to 

```
function __construct() 
```

### Each deprecated

```
PHP Deprecated: The each() function is deprecated. This message will be suppressed on further calls in /Users/sp/Developer/zc157/includes/functions/extra_functions/sfl_functions.php on line 160.
```

Change 

```
while (list($products_id, ) = each($contents)) {
```

to 
```
foreach(array_keys($contents) as $products_id) {
```

If the code looks more like 

```
while(list($key, $value) = each($array))
```

change to 

```
foreach($array as $key => $value)
```

There are several levels of PHP problems, with the least serious being _notices_ and _warnings_. More serious are PHP _errors_, which can cause a blank screen or partially blank screen.  Several common PHP errors are discussed in [this article](/user/troubleshooting/php_debug_logs).
