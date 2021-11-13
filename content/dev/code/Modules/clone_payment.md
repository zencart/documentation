---
title: Cloning a Payment Module
description: Building a new payment module based on an existing one 
---
You can create new Payment Module by making a clone of the closest matching Payment Module to what you are trying to do.
 
As an example, we will consider the `moneyorder` payment module. 
 
Payment Modules have 2 parts: 
  
The code file is located in:  
`/includes/modules/payment/moneyorder.php`
  
The language file is located in:  
`/includes/languages/english/modules/payment/moneyorder.php`
  
To clone this module, for example, to `venmo.php` you would copy the two `moneyorder.php` files to `venmo.php` 

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

These plugins might also help: 
* [Optional Payment Method](https://www.zen-cart.com/downloads.php?do=file&id=1930) 
 
