---
title: Product Weight - changing from pounds (lbs) to kg
description: Localizing data display 
category: localization
weight: 10
---

### 2.0.0 and above
Starting in Zen Cart 2.0, the `SHIPPING_WEIGHT_UNITS` field is added to the configuration table to assist shipping module developers who wish to offer dimensional shipping please see please see [Shipping Dimensions](/user/shipping/shipping_dimensions/) for details. : 

The screen referenced is: 
- [Configuration > Shipping](/user/admin_pages/configuration/configuration_shippingpackaging/)


- When you change `SHIPPING_WEIGHT_UNITS` to kg` 
you will also want to change these language defines in `includes/languages/YOURTEMPLATE/lang.english.php`:  
   - `TEXT_PRODUCT_WEIGHT_UNIT`
   - `TEXT_SHIPPING_WEIGHT`
This way your storefront will show the correct units. See [1.5.8 below](#1.5.8) for details

Your admin will show the weight units which are indicated by the setting of the constant above, `SHIPPING_WEIGHT_UNITS`. Except for the orders detail and products attribute preview pages, to change this you need to change the language defines in `YOURADMIN/includes/languages/lang.english.php`
   - `TEXT_PRODUCT_WEIGHT_UNIT`

The easiest way to do the for zen cart 2.0+ is to create a lang.admin_override.php file in YOURADMIN/includes/languages/english/extra_definitions/ and add the value to the define array. See [UK Customisation - Date to dd/mm/yy, weight to kg, and USD to GBP](/user/localization/uk_language_overide_files/#Admin file changes).

### 1.5.8
Edit `includes/languages/YOURTEMPLATE/lang.english.php`. (Copy `includes/languages/lang.english.php` to `includes/languages/YOURTEMPLATE/lang.english.php` if the override file doesn't already exist.)

Find the following lines of code:

```
    'TEXT_PRODUCT_WEIGHT_UNIT' => ' lbs',
...
    'TEXT_SHIPPING_WEIGHT' => ' lbs',
```

Change the highlighted portions, making sure that the single quote marks are not left out.

### 1.5.7 and below
Edit `includes/languages/YOURTEMPLATE/english.php`.  (Copy `includes/languages/english.php` to `includes/languages/YOURTEMPLATE/english.php` if the override file doesn't already exist.)

Find the following lines of code:

```
define('TEXT_PRODUCT_WEIGHT_UNIT','lbs');

define('TEXT_SHIPPING_WEIGHT','lbs');
```

Change the highlighted portions, making sure that the single quote marks are not left out.