---
title: Add to Cart 
description: Controlling add to cart operation in your store 
category: storefront_pages
weight: 10
---

Unless otherwise noted, the products we will discuss on this page will be assumed to be in stock with the _Call for Price_ flag set to No.

The "Add to Cart" button will *always* appear on the [product info](/user/storefront_pages/product_info/) page.  It may optionally appear on other pages under the following conditions: 

- If the button is configurable on the page in question, it not been turned off.  For example, on the [New Products](/user/storefront_pages/listing_pages/) page, the add to cart button may be turned off using the _Display Product Buy Now Button_ switch on the [Configuration > New Listing](/user/admin_pages/configuration/configuration_newlisting/) page. 

- The product has no attributes, or, the product has only [single-valued attributes](/user/products/single_valued_attributes/). 

If these conditions are not met, the "More Info ..." button is displayed instead of "Buy Now" (or "Add to Cart"), and pressing this button will go to the [product info](/user/storefront_pages/product_info/) page. 

### Limitations on Add to Cart 

Once an add to cart is performed, the following checks are done: 

- the [product quantity minimum, maximum and units](/user/products/product_units/) are checked.  If a violation occurs, the in-cart quantity will be dynamically updated. 
- the [stock tracking configuration 3](/user/running/stock/) is enabled, quantity is not adjusted but checkout will be blocked if stock is insufficient to meet the order requirements. 

