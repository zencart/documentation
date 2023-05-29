---
title: Add to Cart 
description: Controlling add to cart operation in your store 
category: storefront_pages
weight: 10
---

The scope of this FAQ is stores in normal mode (`STORE_STATUS` = 0), and products with: 

- Stock sufficient for a sale (per the [stock settings](/user/running/stock)).
- The _Call for Price_ flag set to "No."

When we say "Add to Cart" it could be: 

- a "Buy Now" button
- a quantity box where the whole page is a form with "Add Selected to Cart" buttons at the top and/or bottom
- a quantity box with an "Add to Cart" button next to it

<hr>

The ability to Add to Cart will *always* be provided on the [product info](/user/storefront_pages/product_info/) page.  

It may optionally appear on other pages (such as listing pages) under the following conditions: 

- If the button is configurable on the page in question, it is turned on.  For example, on the [New Products](/user/storefront_pages/listing_pages/) page, the Add to Cart button may be turned off using the _Display Product Buy Now Button_ switch on the [Configuration > New Listing](/user/admin_pages/configuration/configuration_newlisting/) page.   See [listing page layout](/user/template/listing_page_layout) for more specifics.

- The product has no attributes, or, the product has only [single-valued attributes](/user/products/single_valued_attributes/). 

If these conditions are not met, the "More Info ..." button is displayed instead of "Buy Now" (or "Add to Cart"), and pressing this button will go to the [product info](/user/storefront_pages/product_info/) page. 

### Actions after Add to Cart 

Once an add to cart is performed, the following checks are done: 

- the [product quantity minimum, maximum and units](/user/products/product_units/) are checked.  If a violation occurs, the in-cart quantity will be dynamically updated. 
- the [stock tracking configuration 3](/user/running/stock/) is enabled, quantity is not adjusted but checkout will be blocked if stock is insufficient to meet the order requirements. 

