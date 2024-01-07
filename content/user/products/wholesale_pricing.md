---
title: Wholesale Pricing
description: Using wholesale pricing to add multiple price levels 
category: products
weight: 10
---

Starting in Zen Cart 2.0.0, a new pricing mechanism called Wholesale Pricing is  available in a base install (no plugin required).  To begin using Wholesale Pricing, you just need to enable it under Admin > Configuration > My Store > Wholesale Pricing.  

The remainder of this page assumes that Wholesale Pricing has been enabled.

Wholesale pricing allows you to assign specific customers to a wholesale level, and then provide discounted pricing to those customers.  

Assigning a customer to a wholesale level is done on the [Admin > Customers > Customers](/user/admin_pages/customers/customers/) page by editing a customer record.  The field "Wholesale Level" is used to hold a non-zero number indicating the wholesale level.

![Customer Options](/images/customer_options_wholesale.gif)

Of the stores that use wholesale pricing, many will only have one wholesale level, so this field would always be "1".  But as an example, let's assume a store has three wholesale pricing levels: 
- business customers (level 1), 
- premium business customers (level 2), and 
- a third level for a single company that buys in enormous volumes, Wally World (level 3). 

The value in the Wholesale Level field on the Customer Detail page would thus be:
- 0 (retail customers), 
- 1 (business customers), 
- 2 (premium business customers), or 
- 3 (Wally World).  

We'll look at setting the actual wholesale discounts below. 

Setting wholesale discounts can be done in two ways: 

## Setting Wholesale Price per product 

On the [product editing screen](/user/products/product_edit/), a new field called "Wholesale Price" is shown.  

![Wholesale Pricing Products](/images/wholesale_pricing_product.gif) 

The Wholesale Price field is a dash separated list of discounts - either actual prices or percent off discounts.  

If wholesale level 1 customers get 5% off, level 2 get 10% off, and level 3 get 25% off, the value in the Wholesale Price field on the product editing page would be:

```
5%-10%-25%
``` 

If the regular price of the item is $20, but wholesale level 1 customers only pay $18, level 2 pay $15, and level 3 pay $12, the value in the Wholesale Price field of the product editing page would be:

```
18-15-12
```

If this is a low margin item and all wholesalers only get 5% off, the value in the Wholesale Price field of the product editing page would be:

```
5%
```

(The missing levels get the final discount; this is the same as `5%-5%-5%`.)

## Setting Quantity Discounted Wholesale Prices

On the [Quantity Discounts](/user/products/quantity_discounts/) block of 
[Admin > Catalog > Products Price Manager](/user/admin_pages/catalog/products_price_manager/)
a new column called Wholesale Discount Values is shown. 

![Wholesale Discount Value](/images/wholesale_discount_values.gif) 

The Wholesale Discount Value field is set the same way that Wholesale Price is (see above). 

Customers who are eligible for Wholesale Pricing are not eligible for Sales, Specials and Group Pricing; Wholesale Pricing replaces these other discounting methods. 

