---
title: Quantity Discounts 
description: How do I offer discounts for bulk purchases? 
category: products
weight: 10
---

The 
[Admin > Catalog > Products Price Manager](/user/admin_pages/catalog/products_price_manager/) page allows you to add per product quantity discounts. 

- Select the product
- Press the *Edit Product* button
- Click the *Add 5 Blank Discount Qty* button
- Fill in the details
- Update

Any rows you don't fill in will be removed upon update. 

The screen you see will look like this: 

![Products Price Manager](/images/products_price_manager.png)

Since 2.0.0, if you have [wholesale pricing](/user/products/wholesale_pricing/) enabled, another column appears for setting the wholesale discount value. 

![Wholesale Discount Value](/images/wholesale_discount_values.gif)

The radio button *Discount Qty Applies to Mixed Attributes*  is referring
to the [MIXED ON](/user/products/mixed_on/) setting from the [product editing page](/user/products/product_edit/).

**Note:** Quantity Discounts created using Products Price Manager will discount bulk purchases of a single product.  

- If you need to discount bulk purchases across categories or the entire store, take a look at the [Quantity Discounts plugin](https://www.zen-cart.com/downloads.php?do=file&id=135) in the [Zen Cart Plugins Library](/user/plugins/plugin_library/). 

- If you need to reduce the price of a product *with a specific attribute* when purchased in bulk, look at [**attribute** quantity discounts](/user/products/attribute_pricing/#settings-in-attributes-controller), which are set in the [Attributes Controller](/user/admin_pages/catalog/attributes_controller/#quantity-discounts). 



