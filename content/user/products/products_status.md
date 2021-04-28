---
title: Products Status
description: Enabling and Disabling products 
category: products
weight: 10
---

The [product editing screen](/user/products/product_edit/) allows you to change the product status to either Enabled or Disabled.

An enabled product will appear on the storefront, whereas a 
disabled product will not.

Attempting to navigate to the product page for a product which is disabled will return an HTTP status 404 (page not found).  This is an important consideration, because when it occurs, your customers will no longer be able to see products which may only be temporarily out of stock. 

In addition to changing a product's status by hand in the editing screen, 
a product will automatically be moved to Disabled if the [Products status in Catalog when out of stock](/user/running/stock/) field is set to 0.  For stores where an out of stock condition will be short lived, but who don't want to permit sales when products are not in stock, a good configuration might be  
- Admin > Configuration > Stock > Products status in Catalog when out of stock should be set to = 1
- Admin > Configuration > Stock > Show Sold Out Image in place of Add to Cart = 1 

