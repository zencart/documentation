---
title: Coupons
description: Price reductions and free shipping for customers with a code 
category: order_total
weight: 10
---
Coupons allow you to offer discounts on products and/or shipping. 

If you want to offer a coupon, you need to first enable the coupon system:  Go to: Admin > Modules > Order Total > Discount Coupons (ot_coupon).   If it's not already installed, click _Install Module_ to enable it.  

![Install Coupons](/images/install_coupon.png)

## Creating Coupons

To create coupons, click [Admin > Discounts > Coupon Admin](/user/admin_pages/discounts/coupon_admin/), then _insert_.  

(To edit an existing coupon, use the same steps but press _edit_ at the end instead of _insert_.)  

Fill in the details.  

If the coupon is for a percentage discount, enter the percent sign after the number.  If it is for a fixed amount, just enter the amount. 

If the coupon is for free shipping, check the free shipping box. 

You can enter a coupon code, or if you leave it blank, the system will generate a random code for you.  

Save the coupon.  

Now you can either take the coupon code and manually give it to your customers in advertisements (in print or on your website) or you can click the Email button and send it to a list of customers.  

If you want to set up restrictions so the coupon applies to only to certain products or categories, click the Restrictions button to set them up.  You can do this at a later date if you desire.  

## Coupon Restrictions

To set coupon restrictions, click [Admin > Discounts > Coupon Restrictions](/user/admin_pages/discounts/coupon_restrictions/).  

Coupon Restrictions are designed to limit Discount Coupons to Categories or Products.  

When using Coupon Restrictions, it is best to start with the setting for the Categories of:  
TOP **DENY**  

This starts with the Discount Coupon not allowing any Product or Category of Products to work.  

Next, you would add the Category or Categories allowed, if any.  

Then, you would add the Product or Products allowed, specifically, if not already covered by the Categories.  

These Restrictions will then **ALLOW** or **DENY** the use of the Discount Coupon.  

These Restrictions can then be seen by the Customer via the **Discount Coupons** link in the **Information sidebox**, which opens the Discount Coupon page.  On this page, the customer can enter the Discount Coupon redemption code to see any limits placed on the Discount Coupon.  

## Discount Coupon Page 

This page allows customers to look up any coupon codes they have and see the restrictions (if any) on their coupon.

![Discount Coupon Page](/images/discount_coupon.png)

Looking up a specific coupon code will show the restrictions for that coupon.

![Discount Coupon Restrictions](/images/discount_coupon_lookup.png)

## Redeeming Coupons

When a customer adds something to their cart and proceeds to checkout, they will see a spot to enter a coupon code on the Payments page.  
Once they fill in the code and press Enter, it will be checked for validity, and if it is valid and not restricted against what's in their cart, a Success message will show on the screen, and their order Total will be adjusted appropriately.  

If they wish to remove a coupon, they can enter a different coupon code, or they can type "REMOVE", and press Enter.

![Discount Coupon Entry](/images/discount_coupon_entry.png)

## Coupon Types 

The `coupons` table has a `coupon_type` field. The possible values for coupon_type are: 

- S - Free Shipping
- P - Percent Off 
- E - Percent Off and Free Shipping
- F - Fixed Amount Off
- O - Fixed Amount Off and Free Shipping 
- G - Gift Certificate  


## Display of Coupon Discounts 
Coupon Discounts are shown in the order summary on the checkout payment and
 checkout confirmation pages.  See [price reductions](/user/products/price_reductions/) for details. 
