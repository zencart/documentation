---
title: Constants in Zen Cart
description: Program Constants 
category: code
weight: 10
---

Zen Cart has a group of defined constants (created with the PHP `define` statement) that arise from values in the database, primarily in the `configuration` table. 

The Configuration constants may be seen in the [All Configuration Values](/user/admin_pages/configuration/all/) page.  

The majority of the constants in the configuration tables are created as define strings, based on the `configuration_key` for the row.  So if you look at Admin > Configuration > My Store > Store Name, you can see the `configuration_key` is  `STORE_NAME`.  This means the defined constant is a string called `STORE_NAME`.

The exceptions to the rule of creating string constants are the values in configuration groups 2 and 3, which are the [Minimum Values](/user/admin_pages/configuration/configuration_minimumvalues/)  and [Maximum Values](/user/admin_pages/configuration/configuration_maximumvalues/). 

The Min and Max values can be easily recognized as integer values because almost all of them contain the string `MIN` or `MAX` respectively in their name.  The only exception is `SHOW_NEW_PRODUCTS_LIMIT` (a Max value). 

There are a small number of exceptions to the two rules noted above, which are: 

|Value|Config Group|Screen|Type|
|-----|------------|------|----|
|SECURITY_CODE_LENGTH|16|Admin > Configuration > GV Coupons| Integer| 
|PRODUCTS_MANUFACTURERS_STATUS|3|Admin > Configuration > Maximum Values| String|
|SHOW_SALE_DISCOUNT_DECIMALS|18|Admin > Configuration > Product Info|Integer|

Note that the Max and Min values are converted to Integers at constant creation time in newer versions of Zen Cart in `laravel/app/Models/Configuration.php`.
