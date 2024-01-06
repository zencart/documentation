---
title: PayPal using one account on multiple sites 
description: Consolidating PayPal accounts 
category: payment
weight: 10
---

It is possible to use one PayPal account on multiple carts. 

When you set up the PayPal parameters for each of your Zen Cart sites you can give them the same API credentials used for your single PayPal account. This applies to Express Checkout, Website Payments Pro, Payments Advanced, Payflow Link, and Payments Pro.  
(Or if you're using the not-so-recommended "Payments Standard" module, then you'd use the same email address and PDT token in all your stores.)  

Zen Cart will automatically tell PayPal the address of your store when a payment is submitted, so that the correct store is notified of transaction updates. Each store will see only the orders placed at/with that store.  

The only setup you need to do is make sure that the "Instant Payment Notification" (IPN) setting is **enabled** in your PayPal account profile under Website Payment Receiving Preferences, as explained in the [PayPal setup/troubleshooting guide](/user/payment/paypal_ipn/).

Many people wonder what to do about specifying the **Return URL** or **Notification URL**. Simply set the URLs to the appropriate address for *one* of your stores. It must point to a valid address; that is, a valid address for ANY of your stores. When processing transactions from your various Zen Cart stores, the appropriate address for each store will be substituted automatically by Zen Cart.  

There is one caveat: Your customers will see the name of your PayPal account when making payment, even if that doesn't match your store's name. However, to help differentiate between stores, you can style each store independently by setting the "Page Style" setting in the Zen Cart payment module settings for that PayPal module. You can find more information about setting Page Styles in PayPal by visiting your PayPal account. Your PayPal account name (your business name if it's a business account, or your PayPal email address if it's a premier account) will still show to the customer, but the styling will help make it clear which store they're on, to minimize confusion.  

In summary:  
a) all stores will use the SAME API Credentials (or PayPal email address, and same PDT token, if any),  
b) your PayPal account profile at paypal.com will specify only ONE store for IPN Notification (but Zen Cart will automatically intelligently override for each store)  
c) your PayPal account profile at paypal.com will specify only ONE store for Auto Return (but Zen Cart will automatically override for each store)  
d) You can tell each of your stores to use a certain "Page Style" (from your styles in your PayPal account) to enable different visual branding/appearance to the customer.  

-----------------------  
Alternatively:  
If you have a business need to separate your two stores enough that separate PayPal Business Accounts make sense, you'll need to have separate bank accounts and separate Tax ID numbers (TINs) in order to create additional PayPal accounts.
