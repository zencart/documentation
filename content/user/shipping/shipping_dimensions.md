---
title: Shipping Dimensions 
description: product dimensions and shipping configuration 
category: shipping
weight: 10
---

Starting in Zen Cart 2.0, the following fields are added to assist shipping module developers who wish to offer dimensional shipping: 

|Screen|Table|Field|Description|Other|
|------|-----|----|-----|--------|
|Product Edit|products|`products_length`|Length of product| |
|Product Edit|products|`products_width`|Width of product| |
|Product Edit|products|`products_height`|Height of product| |
|Product Edit|products|`products_ready_to_ship`|Does product ship in its own box||
|Configuration > Shipping|configuration|Shipping Weight Units|Is products_weight expressed in pounds or kg? | Configuration key is `SHIPPING_WEIGHT_UNITS`| 
|Configuration > Shipping|configuration|Shipping Dimension Units|Are products length, width and height expressed in inches or centimeters? | Configuration key is `SHIPPING_DIMENSION_UNITS`| 

The screens referenced above are: 
- [Product Edit](/user/products/product_edit/)
- [Configuration > Shipping](/user/admin_pages/configuration/configuration_shippingpackaging/)


Metric users please note: 
- When you change `SHIPPING_WEIGHT_UNITS` to `kg` 
you will also want to change these language defines in `includes/languages/YOURTEMPLATE/lang.english.php`:  
   - `TEXT_PRODUCT_WEIGHT_UNIT`
   - `TEXT_SHIPPING_WEIGHT`
This way your storefront will show the correct units. 

Your admin will show the units which are indicated  by the setting of the two constants above, `SHIPPING_WEIGHT_UNITS` and `SHIPPING_DIMENSION_UNITS`.

The screenshot below shows the new fields in the Product Edit and Configuration > Shipping screens: 

![Shipping Dimension Fields](/images/dimensions.png)
 
