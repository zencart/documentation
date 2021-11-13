---
title: Cloning a Shipping Module
description: Building a new shipping module based on an existing one 
---
You can create new Shipping Module by making a clone of the closest matching Shipping Module to what you are trying to do.
 
As an example, we will consider the `flat` shipping module. 
 
Shipping Modules have 2 parts: 
  
The code file is located in:  
`/includes/modules/shipping/flat.php`
  
The language file is located in:  
`/includes/languages/english/modules/shipping/flat.php`
  
To clone this module, for example, to `flatfree.php` you would copy the two `flat.php` files to `flatfree.php` 

**Note:** Be sure the filename you choose does not have an underscore (`_`) in it.
  
Next, you need to change all occurrences of the strings `flat` and `FLAT` as follows: 

OLD | NEW
----|----
`flat` | `flatfree` 
`FLAT` | `FLATFREE` 

These identifiers are case sensitive. 
  
These words are written separately or within the constants such as:  
  

```
class flat {
... 
$this->code = 'flat';
... 
$this->title = MODULE_SHIPPING_FLAT_TEXT_TITLE;
```

becomes 

```
class flatfree {
...
$this->code = 'flatfree';
...
$this->title = MODULE_SHIPPING_FLATFREE_TEXT_TITLE;
```

Once you have cloned the module then you can alter how it calculates shipping to the method that you need.   This calculation is done in the `quote()` method. 
  
Flat does not have complicated logic to compute a quote; it 
uses a single figure. 
  
To see examples of quote calculations that are more complex, you might look
at the `items.php` Shipping Module.
  

Cloning or creating a Shipping Module to function the way you need it is not too difficult if you just work through the steps on paper then recreate the same steps within the `quote()` function. 
 
These forum threads might also give you ideas: 
* [Thread: Additional Shipping Option - Flat Rate Per Item](https://www.zen-cart.com/showthread.php?26216-Additional-Shipping-Option-Flat-Rate-Per-Item)
* [Thread: How do I set 2 flat shipping rates to 2 different zone?](https://www.zen-cart.com/showthread.php?41751-How-do-I-set-2-flat-shipping-rates-to-2-different-zone) 
 
