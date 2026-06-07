---
title: Cloning a Payment Module
description: Building a new payment module by cloning an existing one
weight: 50
aliases:
  - /dev/modules/clone_payment/
---

**Note:** These instructions are for Zen Cart 1.5.8 and above.  For Zen Cart 1.5.7 and below, please see [Cloning a Payment Module in 1.5.7 and below](/dev/modules/clone_payment_157/).

You can create new Payment Module by making a clone of the closest matching Payment Module to what you are trying to do.
 
As an example, we will consider the `moneyorder` payment module. 
 
Payment Modules have 2 parts: 
  
The code file is located in:  
`/includes/modules/payment/moneyorder.php`
  
The language file is located in:  
`/includes/languages/english/modules/payment/lang.moneyorder.php`
  
To clone this module, for example, to `venmo.php` you would:
- copy `moneyorder.php` to `venmo.php`
- copy `lang.moneyorder.php` to `lang.venmo.php`

**Note:** Be sure the filename you choose does not have an underscore (`_`) in it.
  
Next, you need to change all occurrences of the strings `moneyorder` and `MONEYORDER` as follows: 

OLD | NEW
----|----
`moneyorder` | `venmo` 
`MONEYORDER` | `VENMO` 

These identifiers are case sensitive. 
  
These words are written separately or within the constants such as:  
  

```
class moneyorder {
... 
$this->code = 'moneyorder';
... 
$this->title = MODULE_PAYMENT_MONEYORDER_TEXT_TITLE; 
```

becomes 

```
class venmo {
...
$this->code = 'venmo';
...
$this->title = MODULE_PAYMENT_VENMO_TEXT_TITLE;
```

Be sure to make this change in the `remove()` function as well.

These plugins might also help: 
* [Optional Payment Method](https://www.zen-cart.com/downloads.php?do=file&id=1930) 
 
