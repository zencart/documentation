---
title: Displaying Custom Fields 
description: How to show the custom fields you have added to the database
category: code
weight: 10
---

Once you have finished adding a field to the database, you will need to figure out where you want to display it, and write the code to do that.   Here are some guidelines. 

## Case 1: New field in products table

a) Adding the new field to the [product_info page](/user/products/product_info/): 
- Modify `includes/modules/pages/product_info/main_template_vars.php` to retrieve the field and create a variable to store it. 
- Modify `includes/templates/YOURTEMPLATE/templates/tpl_product_info_display.php` to show the variable. 

b) Adding the new field to the [product listing](/user/template/product_listing_page_configuration/) page: 

- Modify `includes/modules/pages/index/main_template_vars.php` to retrieve the new field.
- Modify `includes/modules/YOURTEMPLATE/product_listing.php` to display the field.

(Some people shortcut this process by skipping the first file and just doing the query in the second file.) 

## Case 2: New field in orders table
If you add a field to the orders table which is set during order creation, add the field to `includes/classes/order.php` in the `query()` method. 

Then you can reference it as needed in 

- tpl_account_default.php
- tpl_account_history_default.php
- tpl_account_history_info_default.php

On the admin side, you may also wish to reference it in 

- admin/invoice.php
- admin/orders.php
- admin/packingslip.php

In the `query()` method from `includes/classes/order.php`, add it to whatever array makes sense (`info`, `customer`, or `delivery`), then reference it in any of the files above the same way other fields in that array are referenced.

## Related Articles 
- [Adding a field to the products table](/dev/code/add_field_products/)
