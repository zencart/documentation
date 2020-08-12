---
title: Fixing PHP Warnings and Deprecated messages 
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

