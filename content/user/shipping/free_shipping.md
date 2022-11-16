---
title: Free Shipping
description: Handling delivery when shipping is not required
category: shipping 
weight: 10
---

Note: During Checkout, the Shipping Selection page is automatically skipped if all products in the cart are virtual.  

## How do I tell the shopping cart that shipping does not apply?

Individually set products as `free shipping` by visiting the [product editing screen](/user/products/product_edit/) for each one, and setting radio button `Always Free Shipping` to `Yes`. 

Then enable the `FREE SHIPPING!` module on [Admin > Modules > Shipping](/user/admin_pages/modules/shipping/). 

This will allow checkout to totally bypass the shipping page.

---

## How do I make shipping free?

There are several ways to offer free shipping: 

- mark the product as free-shipping (see above)
- mark the product as virtual 
- associate downloads with the product and mark it as free shipping
- create coupons that have Free Shipping as part of the discounting they provide
- use the Free Options shipping module, which offers free-shipping based on special criteria you can set (see below)
- set the product weight to 0, and set [Order Free Shipping 0 Weight Status](/user/admin_pages/configuration/configuration_shippingpackaging/#order_free_shipping_0_weight_status) 

--- 

## How do I enable free shipping for orders more than $XX?

Go to [Admin > Modules > Order Total](/user/admin_pages/modules/order_total/).

Then select *Shipping* from the list. 
If the module is not installed click the install button. 

Click edit to configure the criteria to allow free shipping.

## How can I allow free shipping but still show other shipping options as choices?

You may wish to offer free shipping but still present paid shipping options,for example if your other shipping options are expedited for a higher fee.

If this case, use the `Free Shipping Options` module on [Admin > Modules > Shipping](/user/admin_pages/modules/shipping/). 

You may configure shipping to be free under any of these conditions: 

- Always 
- Order Total less than or greater than a specified value 
- Order Weight less than or greater than a specified value 
- Order Item Count less than or greater than a specified value

Then your customer would see something like this: 

![Free plus paid shipping](/images/free_plus_shipping.png)

**Note:** If you are doing this, be sure to set `Always Free Shipping` on the [Product Editing page](/user/products/product_edit/) to false. 

## My store shows free shipping but I don't want it! 

You may need to do one or more of these things. 

- Go to [Admin > Modules > Order Total](/user/admin_pages/modules/order_total/), and select *Shipping*, then press Edit.   If *Allow Free Shipping* is true, turn it to false, or if you simply want to raise the  threshold, update the field *Free Shipping For Orders Over*. 

- Go to [Admin > Modules > Shipping](/user/admin_pages/modules/shipping/), and adjust or remove `Free Shipping Options` and/or `FREE SHIPPING!`. 
 
- Go to [Admin > Configuration > Shipping/Packaging](/user/admin_pages/configuration/configuration_shippingpackaging) and set `Order Free Shipping 0 Weight Status` to 0.  Or, if you wish zero weight packages to generally be shipped free, but you're finding some products are zero weight and shouldn't be, you'll want to find all of those and fix them.  See options below for finding these misconfigured products. 

## How do I find products incorrectly configured with zero weight? 

- You could [build a report](/dev/code/reports/) to show items with zero weight. 
- You could [build a dashboard widget](/dev/code/widget/) to display zero weight items on your admin home page.
 
- You could run a SQL query from phpMyAdmin.  
```
SELECT p.products_id, pd.products_name FROM products p, products_description pd WHERE p.products_id = pd.products_id AND p.products_weight = 0 AND products_virtual = 0; 
```

