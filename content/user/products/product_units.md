---
title: Product Units 
description: Min and Max Quantities and Units 
category: products
weight: 10
---

The [product editing screen](/user/products/product_edit/) shows the following fields related to sale quantities. 

![product units](/images/product_units.png)

- Product Quantity Box Shows just determines whether to show the quantity box on pages which allow the product to be purchased, such as [product info](/user/products/product_info) page, and possibly also the [listing pages](/user/products/product_listing/).

- Product Qty Minimum is the lowest number of this product which may be purchased.

- Product Qty Maximum is the highest number of this product which may be purchased.

- Product Qty Units is used when the product needs to be purchased in bundles.

- Product Qty Min/Unit Mix is covered in [What does MIXED ON mean?](/user/products/mixed_on/).

For example, if 

- Product Qty Minimum = 500 

- Product Qty Units = 250 

Then purchases of 500, 750, 1000 and so on would be accepted. 

Attempting to purchase 501 of this product would be shown as an error on the shopping cart page, and checkout would be blocked until the quantity was fixed.

For Product Qty Maximum, the values 0 and 1 are special: 

- when set to 0 (the default), there is no limit on the number that may be purchased.
- when set to 1, only one of the product may only be purchased, so there is no quantity box displayed next to the add to cart button.


