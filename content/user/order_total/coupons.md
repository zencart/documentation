---
title: Coupons
description: Zen Cart Coupons
category: order_total
weight: 10
---
If you want to offer a coupon, you need to first enable the coupon system:  

Go to: Admin->Modules->Order Total->Discount Coupons (ot_coupon).   
If it's not already installed, click Install to enable it.  

## Creating Coupons

Now, in your Admin area, you have a menu item entitled "Discounts".  Click on the Coupon Admin option.  

Next, you create a coupon by clicking Insert.  (Or Edit to edit an existing coupon.)  
Fill in the details.  
If the coupon is for a percentage discount, enter the percent sign after the number.  
If the coupon is ONLY for free shipping, check the free shipping box. (This ignores all the % or amount discounts, and makes the coupon ONLY apply to shipping.)  
You can enter a coupon code, or if you leave it blank, the system will generate a random code for you.  
Save the coupon.  

Now you can either take the coupon code and manually give it to your customers in advertisements (in print or on your website) or you can click the Email button and send it to a list of customers.  

If you want to set up restrictions so the coupon applies to only to certain products or categories, click the Restrictions button to set them up.  You can do this at a later date if you desire.  

## Coupon Restrictions

Coupon Restrictions are designed to limit Discount Coupons to Categories or Products.  

When using Coupon Restrictions, it is best to start with the setting for the Categories of:  
TOP **DENY**  

This starts with the Discount Coupon not allowing any Product or Category of Products to work.  

Next, you would add the Category or Categories allowed, if any.  

Then, you would add the Product or Products allowed, specifically, if not already covered by the Categories.  

These Restrictions will then **ALLOW** or **DENY** the use of the Discount Coupon.  

These Restrictions can then be seen by the Customer via the **Discount Coupons** link in the **Information sidebox** where the customer can enter the Discount Coupon redemption code to see any limits placed on the Discount Coupon.  

## Redeeming Coupons

When a customer adds something to their cart and proceeds to checkout, they will see a spot to enter a coupon code on the Payments page.  
Once they fill in the code and press Enter, it will be checked for validity, and if it is valid and not restricted against what's in their cart, a Success message will show on the screen, and their order Total will be adjusted appropriately.  

If they wish to remove a coupon, they can enter a different coupon code, or they can type "REMOVE", and press Enter.
