---
title: Categories/Products (Products Level)
category: admin_pages
weight: 12
---

**Note:** If you are looking for the Categories screen showing categories, please [see this page](/user/admin_pages/catalog/categories/). 

If you are at a level where the Categories screen only shows products, you'll see a table with a number of rows that will look something like this: 

![admin categories products](/images/admin_product_listing_rows.png) 

## ID and Name

The first field on the left hand side is the numeric product ID.

Next to that is a field containing the product name, with an icon to the left of the name.  The icon will open the category in the storefront (allowing you to check the appearance of images and text related to the product).  

## Status Icons

Under the Status column header, you'll see an icon that is either red or green, with an optional yellow icon.

- Red means the product is disabled
- Green means the product is enabled
- Yellow means the product is [linked](/user/products/linked_product/)

## Action Icons 
There are a set of action icons on the right.

<img src="/images/products_icons.png" alt="Admin Product Listing Icons" style="float: right" /> 
<br clear="all" />

These icons allow you to perform the following actions:

Button | Action 
-------|-------
Pencil | [edit a product](/user/products/product_edit/) - update all the fields for a product 
Trash Can | [delete a product](/user/products/product_management_admin/#deleting-a-product) - remove a product from the catalog 
M | [move a product](/user/products/product_management_admin/#moving-a-product) - change the product's parent category
C | [copy a product](/user/products/product_management_admin/#copying-a-product) - duplicate the product or create a [linked product](/user/products/linked_product/)
A | use the [attributes controller](/user/admin_pages/catalog/attributes_controller/)
Dollar Sign | use the [products price manager](/user/admin_pages/catalog/products_price_manager/)
Asterisk | use the [meta tags editor](/user/admin_pages/catalog/products_meta_tags_editor/). 


Some of these icons change color depending on the product:

Button | Meaning
-------|-------
![blue A](/images/admin_button_blue_a.png) | Product has attributes 
![black A](/images/admin_button_black_a.png) | Product does not have attributes 
![orange star](/images/admin_button_orange_star.png) | Product has custom meta tags 
![white star](/images/admin_button_white_star.png) | Product does not have custom meta tags 
![green dollar](/images/admin_button_green_dollar.png) | Product may be added to cart 
![white dollar](/images/admin_button_white_dollar.png) | Product may not be added to cart 
![dark green dollar](/images/admin_button_dark_green_dollar.png) | Product has quantity discounts and may be added to cart (since Zen Cart 1.5.8)

