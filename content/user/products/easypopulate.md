---
title: EasyPopulate 
description: Creating products from a CSV 
category: products
weight: 10
---

### EasyPopulate 

Rather than enter products one-by-one in the admin panel, some storeowners prefer to use tools that will import a CSV containing product information.  One such tool is called EasyPopulate.  Other spellings of this name include:

- "Easy Populate"
- "EZPopulate" 
- "EZ-Populate" 

You can find [EasyPopulate in the Plugins Library](https://www.zen-cart.com/downloads.php?do=file&id=2069).  Many versions exist; the one version linked here is the most recent and well supported. 

Notes on using EasyPopulate: 
- Loading data is a two-step process: first you upload the file, then you import the data.
- The key for product data imports is the model number field.  You may wish to use [Find Duplicate Models](https://www.zen-cart.com/downloads.php?do=file&id=1323) as an aid to making your model numbers unique if you suspect you have duplicates. 

## DbIo - an alternative to EasyPopulate 

Please see [Database I/O Manager (DbIo)](https://www.zen-cart.com/downloads.php?do=file&id=2091). 


## Custom Population Scripts

Many stores will use custom scripts that read feed files, externally generated CSVs and other sources of product data.  Some things to consider if you are building or maintaining such a tool:

- Be sure to create entries in the `products_to_categories` table that map each product to at least one category.
- Be sure to run [Products Price Sorter](/user/admin_pages/tools/store_manager/) after changing prices so sort by price will work properly.  The programmatic way to do this is by calling `zen_update_products_price_sorter()`.


