---
title: UK Customisation - Date to dd/mm/yy, weight to kg, and USD to GBP 
description: Minimum changes necessary for localizing data display for UK. 
category: localization
weight: 10
---

Starting in zen cart 1.5.8 that language files were changed to make it easier to override the default language definitions. The following are the minimum changes necessary to move from US currency, weight and date formats to the UK formats.

# Storefront changes.

### 1. Open file `includes/languages/YOURTEMPLATE/lang.english.php`

### 1a. If this file doesn't exist, create the file `includes/languages/lang.english.php`) and copy in the following code
 
```
<?php
// -----
// Since the languages are now loaded via classes, the $locales definition
// needs to be globalized for use in payment-methods (e.g. paypalwpp) and
// other processing.
//
global $locales;
$locales = ['en_GB', 'en_GB.utf8', 'en', 'English_United Kingdom.1252'];
 @setlocale(LC_TIME, $locales);
$define = [
    'DATE_FORMAT' => 'd/m/Y',
    'DOB_FORMAT_STRING' => 'dd/mm/yyyy',
    'ENTRY_DATE_OF_BIRTH_ERROR' => 'Is your birth date correct? Our system requires the date in this format: DD/MM/YYYY (eg 21/05/1970) or this format: YYYY-MM-DD (eg 1970-05-21)',
    'ENTRY_DATE_OF_BIRTH_TEXT' => '* (eg. 21/05/1970 or 1970-05-21)',
    'LANGUAGE_CURRENCY' => 'GBP',
    'TEXT_PRODUCT_WEIGHT_UNIT' => 'kg',
    'TEXT_SHIPPING_WEIGHT' => 'kg',
];

return $define;
```

**NOTE:** as the UK official language is English it is only necessary to add definitions that you want to override to this file. So if you want to change to the UK spelling of catalogue you could add the line

```
   'TEXT_DATE_ADDED' => 'This product was added to our catalogue on %s.',
```

to the $define array.

Now go to [Admin file changes](#Admin file changes) below.

### 1b. If the file does exist

#### i. find this line (set the server local)

```
$locales = ['en_US', 'en_US.utf8', 'en', 'English_United States.1252'];
```
and replace with:  

```
$locales = ['en_GB', 'en_GB.utf8', 'en'];
```

#### ii. find these lines (change date order)

```
    'DATE_FORMAT' => 'm/d/Y',

    'DOB_FORMAT_STRING' => 'mm/dd/yyyy',
```

and replace with:  

```
    'DATE_FORMAT' => 'd/m/Y',

    'DOB_FORMAT_STRING' => 'dd/mm/yyyy',
```

#### iii. find these lines  (change date descriptions)

```
    'ENTRY_DATE_OF_BIRTH_ERROR' => 'Is your birth date correct? Our system requires the date in this format: MM/DD/YYYY (eg 05/21/1970) or this format: YYYY-MM-DD (eg 1970-05-21)',
    'ENTRY_DATE_OF_BIRTH_TEXT' => '* (eg. 05/21/1970 or 1970-05-21)',
```

and replace with:  

```
    'ENTRY_DATE_OF_BIRTH_ERROR' => 'Is your birth date correct? Our system requires the date in this format: DD/MM/YYYY (eg 21/05/1970) or this format: YYYY-MM-DD (eg 1970-05-21)',
    'ENTRY_DATE_OF_BIRTH_TEXT' => '* (eg. 21/05/1970 or 1970-05-21)',
```

#### iv. find these lines (change default currency)

```
'LANGUAGE_CURRENCY' => 'GBP',
```

and replace with

```
'LANGUAGE_CURRENCY' => 'GBP',
```

#### v. zen cart 2.0+ find these lines (change weight unit)

```
'TEXT_PRODUCT_WEIGHT_UNIT' => 'lbs',
```

and replace with

```
'TEXT_PRODUCT_WEIGHT_UNIT' => 'kg',
```

#### vi. zen cart 2.0+ find these lines (change shipping weight unit)

```
    'TEXT_SHIPPING_WEIGHT' => 'lbs',
```

and replace with

```
    'TEXT_SHIPPING_WEIGHT' => 'kg',
```

# Admin file changes

### 1. Create file `admin/includes/languages/english/extra_definitions/lang.admin_overrides.php`

(If it already exists simply add the lines below excluding the first line `<?php` removing any duplicate definitions)

### 1a. insert the following lines

```
<?php
 @setlocale(LC_TIME, ['en_GB', 'en_GB.utf8', 'en']); 

$define = [    
    'DATE_FORMAT' => 'd/m/Y',
    'DATE_FORMAT_SHORT' => '%d/%m/%Y',
    'DATE_FORMAT_SPIFFYCAL' => 'dd/MM/yyyy',
    'ENTRY_DATE_OF_BIRTH_ERROR' => '&nbsp;<span class="errorText">(eg. 21/05/1970)</span>',
    'PHP_DATE_TIME_FORMAT' => 'd/m/Y H:i:s',
    'TEXT_PRODUCT_WEIGHT_UNIT' => 'kg',
];
return $define;
```

You can add other items to the `$define` array to set any other values defined in YOURADMIN/languages/lang.english.php and/or all the 'lang.' files in YOURADMIN/languages/english/

# Admin configuration changes (zen cart 2.0+)

### 1 change shipping weight and size 

- [Configuration > Shipping](/user/admin_pages/configuration/configuration_shippingpackaging/)

Having logged in to your admin account 

### 1a. goto [Admin > Configuration > Shipping/Packaging](/user/admin_pages/configuration/configuration_shippingpackaging/)

#### i. find the value Shipping Weight Units

change to kg

#### ii. find the value Shipping Dimension Units

change the value to centimeters

### 1b. go to [Admin > Localization > Currencies](/user/admin_pages/localization/currencies/).  

If your currency is in the list which is shown, click your currency, click Edit and check the box labelled *Set as default*.  Then click Save.  

If your currency is *not*  in the list which is shown, click the *New Currency* button. Fill in the information appropriate for your currency and check the box if it is to be the default for your shop. Click the *Insert* button, then after the page refreshes, click the *Update Currencies* button.

Be sure to click the *Update Currencies* button on at least a weekly basis to update all exchange rates.

If you wish to allow a dropdown menu for shoppers to change the store's displayed prices in that currency, you can enable the [Currencies Sidebox](/user/sideboxes/sidebox_list/#currencies) to appear in either the left or right sidebars.



And that's it, you're done!  
