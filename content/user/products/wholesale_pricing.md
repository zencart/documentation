---
title: Wholesale Pricing
description: Using wholesale pricing to add multiple price levels 
category: products
weight: 10
---

Starting in Zen Cart 2.0.0, a new pricing mechanism called Wholesale Pricing is  available in a base install (no plugin required).  To begin using Wholesale Pricing, you just need to enable it under Admin > Configuration > My Store > Wholesale Pricing.  

The remainder of this page assumes that Wholesale Pricing has been enabled.

Wholesale pricing allows you to assign specific customers to a wholesale pricing group, and then provide discounted pricing to those customers.  

Assigning a customer to a wholesale pricing group is done on the [Admin > Customers > Customers](/user/admin_pages/customers/customers/) page by editing a customer record.  The field "Wholesale Level" is used to hold a non-zero number indicating the wholesale pricing group.

![Customer Options](/images//customer_options_wholesale.gif)

Setting wholesale discounts can be done in two ways: 

- On the [product editing screen](/user/products/product_edit/), a new field called "Wholesale Price" is shown.  

![Wholesale Pricing Products](/images/wholesale_pricing_product.gif) 

- On the [Quantity Discounts](/user/products/quantity_discounts/) block of 
[Admin > Catalog > Products Price Manager](/user/admin_pages/catalog/products_price_manager/)
a new column called Wholesale Discount Values is shown. 

![Wholesale Discount Value](/images/wholesale_discount_values.gif) 

Customers who are eligible for Wholesale Pricing are not eligible for Sales, Specials and Group Pricing; Wholesale Pricing replaces these other discounting methods. 

