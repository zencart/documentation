---
title: Products Status
description: Enabling and Disabling products 
category: products
weight: 10
---

The [product editing screen](/user/products/product_edit/) allows you to change the product status to either Enabled or Disabled.

An enabled product will appear on the storefront, whereas a disabled product will not (by default).

Attempting to navigate to the product page for a product which is disabled will return an HTTP status 404 (not found), with the message "product not found".  This is an important consideration, because when it occurs, your customers will no longer be able to see products which may only be temporarily out of stock. 

In addition to changing a product's status by hand in the editing screen, 
a product will automatically be moved to Disabled if the [Products status in Catalog when out of stock](/user/running/stock/) field is set to 0.  For stores where an out of stock condition will be short lived, but who don't want to permit sales when products are not in stock, a good configuration might be  
- Admin > Configuration > Stock > Products status in Catalog when out of stock should be set to = 1
- Admin > Configuration > Stock > Show Sold Out Image in place of Add to Cart = 1 

## Changing the behavior of Disabled Products 

In 1.5.7a, a new configuration value called [Disabled Product Status for Search Engines](/user/admin_pages/configuration/configuration_stock/#disabled_product_status_for_search_engines) was added. When this option to set to 'true', the product info page for a disabled product *will* be shown, and an HTTP status 200 (OK) will be returned.  

Disabled products will still be excluded from listing pages; this config only affects the product info page.

Shopowners who set this config to true will likely want to modify their `product_info` templates to detect disabled status and take action: 
- if `products_quantity` is > 0, the add to cart button is shown, which is undesirable since the cart won't actually honor an add to cart request for a disabled product. 
- if `products_quantity` is <= 0, the sold out message is shown, which may or may not be desirable depending on why the product was disabled. 
- it may be desirable to state whether the unavailability is temporary or permanent.
- if possible, a link to an alternative or substitute product may prevent the customer from going elsewhere. 

