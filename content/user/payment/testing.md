---
title: Testing your payment module
description: Best practices for being sure a payment module is ready to use 
category: payment
weight: 10
---

This is the best way to test a new payment module: 

- Have you ever run a transaction through your store before?  If not, STOP and test the simplest possible case first.  Enable the Check/Money Order payment method (only temporarily if you are not planning to use it live), and run a transaction using this payment method.  Be sure to get all the way to the the [Checkout Success](https://docs.zen-cart.com/user/storefront_pages/checkout/#success-page) page.  Now you know your cart is ready for more advanced testing. 
- Configure the new payment module for production/live (not test or sandbox) using the instructions provided. 
- Create an item in Admin > Catalog > Categories/Products called "Test Product" priced at $1.00, no tax, always free shipping. 
- Ensure that either the FREE SHIPPING or Store Pickup shipping module is enabled. 
- Add the new item to your cart and check out.  
- If the new module you are testing uses credit cards, *use a real credit card*.  Don't try to short-cut it using a test card number.  You want to be sure it really works. 
- Go all the way through to the [Checkout Success](https://docs.zen-cart.com/user/storefront_pages/checkout/#success-page).  If you have the skills, it's a good practice to use Chrome and open the Console in the [Inspect dialog](/user/running/inspect/) to see if your new module has any JavaScript problems.  Carefully check for any debug logs that might have been created.  
- If you get all the way to Checkout Success, and can see the order in your [Admin Orders page](https://docs.zen-cart.com/user/admin_pages/customers/orders/), you can be confident your new module works. 

Please note what these steps do *not* say: 
- They don't say "Use sandbox mode."  DO NOT USE SANDBOX MODE.  You are introducing a bunch of new variables, and you're not testing what your customers will use.  And you will need to test production mode anyhow, so don't waste time. 
- They don't say "stop at the checkout confirmation page; that's good enough."  It's important to go all the way through to the checkout success page.  Lots of logic is executed at the final checkout step, and you want to be sure it all works properly. 
- They don't say "be sure to refund your one dollar transaction." Don't refund more than at most one of these test transactions.  Your payment provider may lose patience with you if they see a bunch of refunds.  The item is only a dollar, don't worry about it.


