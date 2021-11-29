---
title: Adding a child table to the products table 
description: How to add a table linked to the products table by a foreign key 
category: code
weight: 10
---

As an alternative to [adding a field](/dev/code/add_field_products/), you may wish to create a child table. 

You can see cases where this is already done in Zen Cart: the `products_description` table is a child table of the `products` table, linked by `products_id`.

Why would you create a child table rather than just extend the products table?  Here are some scenarios: 

- Some products may not need a child table entry. 
- Some products may need multiple child table entries. 
- Child table entries are required for each supported language. 

The decision is yours, based on your needs.  

Considerations: 
- You will need to build code to handle adding, updating and deleting this data.
- What happens when a product is deleted?  You may wish to modify `admin/includes/modules/delete_product_confirm.php` or the `zen_remove_product` function. 
- What happens when a product is copied?  You may wish to modify `admin/includes/modules/copy_product_confirm.php`. 

Then you will need to [customize your template to display the new field](/dev/code/displaying_custom_fields/). 
