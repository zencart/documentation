---
title: PayPal Standard, Express and Pro - what's the difference? 
description: Zen Cart PayPal Standard, Express and Pro - what's the difference? 
category: payment
weight: 10
---

If you have already decided to use PayPal Express, see [Setup instructions for PayPal Express Checkout](/user/payment/paypal_express_checkout/). 

Zen Cart recommends using Express Checkout instead of PayPal Standard.  Another option is a newer module, called [PayPal RESTful](/user/payments/paypal_restful/), which will be available soon, and will eventually replace both PayPal Express and PayPal Website Payments Pro.

**PayPal Express Checkout**  gives the customer two options: They can jump over to the PayPal site to login to their account BEFORE completing checkout on your store (which allows them to select their address information there and never have to re-type their address details on YOUR site, thus the "express" part of the transaction) and then choosing shipping choices and discounts/coupons etc before completing the order ....... OR they can go to the PayPal site to login to their account AFTER making shipping/payment/coupon selections on your site (and creating an account on your store and typing their address info on your store), much like they do with Standard.    

<u>**With Express Checkout, the customer can pay without having a PayPal account**</u> (as long as you have "PayPal Account Optional" enabled inside your PayPal merchant account settings:  Profile > Hosted Payment Settings > Website Payments Preferences > PayPal Account Optional = ON), except for merchants/customers in China.  

One important benefit is that Express Checkout does not rely entirely on the IPN communications to your store in order to release the order. Instead, it stores the order immediately when payment is completed. It doesn't have to rely on the PayPal server to talk to your server in order to store the order.  Granted, you will still want PayPal's server to be able to send IPN updates to you for any orders, in case you do refunds or adjustments to the order... so that those updates are reflected in your store's order history.  

[PayPal Standard is no longer recommended](/user/payment/paypal_standard).  You should NOT be using Payments Standard; you should be using Express Checkout which is far more reliable.

Express Checkout has all the same features as PayPal Standard, but is more reliable because it completes the transaction directly while the customer is actively engaged on your site. It supports all the currencies, payment methods, etc, just the same, but more efficiently. There is no monthly fee for using Express Checkout.  

PayPal sees Express Checkout as a payment option that's offered <u>in addition to</u> other payment choices such as a credit card gateway, and that adding Express is a way to allow PayPal members a very quick and easy way to pay using their PayPal account. PayPal also believes [Express Checkout improves conversions/sales.](https://www.paypal-marketing.com/paypal/html/partner/na/pdf/Winning%20at%20Checkout.pdf) Many merchants do use Express Checkout as their sole payment processing option, even without a credit card gateway.  

Many merchants also add Website Payments Pro:  

**Website Payments Pro** appears to the customer only as a couple fields to enter their credit card number directly on your website. They have no idea that in the background you're processing their card via PayPal.  They have to make an account on your site, and supply the address details, but once they confirm the order, the payment is collected immediately and the order saved. It doesn't rely on IPN to release the order. However, it does store any transaction updates done on the PayPal end such as refunds etc as long as IPNs can be received by your server.   Website Payments Pro is currently only offered in the USA, UK, and Canada. A monthly service charge applies, and there is an account application process and credit check to complete before the feature can be activated on your account.  PayPal Express Checkout must be enabled in order for Website Payments Pro to be offered on your site.  

PayPal sees Website Payments Pro as a payment gateway for handling credit cards. That's exactly what it is. Coupled with Express Checkout, it gives your customers the maximum amount of choice about how to pay: either by credit card directly on your site, or by using their PayPal account to submit payment.  

**PayPal Payments Advanced** is a new service offered starting in 2012, and requires an addon module in order to use it. Details about this service can be found on the PayPal website. There is a monthly fee to use this service, which is only available in USA.  

**PayPal Payments Standard** (formerly referred to as "PayPal IPN" in older versions of Zen Cart, or as "Website Payments Standard") takes the customer to PayPal's site AFTER the ENTIRE checkout in order to make payment.  The customer can pay without having a PayPal account (depending on what country YOU are in ... PayPal limits that feature for some countries).  After the payment is completed, your store is notified of the completed payment, after which time the order is stored in your database.  When paying with PayPal Standard, if the customer pays without making a PayPal account and closes their browser when presented with the invitation to make one, your store sits in limbo and never gets the order (due to a bug in PayPal's logic, which they've not fixed yet).  If they DO have OR make a PayPal account, you get the notification and the order is stored in your database.   

IF there is any problem in PayPal's ability to communicate to your server, you will never see the order in your store (or receive the confirmation email from your store), because it relies entirely on PayPal's server being able to talk to your server in order to store the order.  

PayPal sees PayPal Payments Standard as a solution for merchants wanting to collect single payments especially if they have no other payment method available. There is no monthly fee for Standard (or Express Checkout)

Zen Cart recommends using PayPal Express Checkout over Website Payments Standard.  

### Other PayPal Services 

**PayPal RESTful** is a new integration which uses PayPal's latest API.  See [PayPal RESTful](/user/payment/paypal_restful) for more details.

**Payflow Pro**  is essentially *only* a merchant account.  Transactions conducted via Payflow Pro (for US Merchants) do not appear in your PayPal account ... instead, they are forwarded directly to your merchant bank account.  Basically, Payflow Pro is just like any other traditional payment gateway (akin to Authorize.net etc). In North America you can connect the Payflow Pro service to your own merchant bank account. In the UK, the Payflow Pro service is actually bundled as a hybrid service with Website Payments Pro, connecting all the transactions to your UK PayPal account, and all monies are deposited to your PayPal account, instead of directly to your bank account. There is a monthly fee for using this service.  

Zen Cart does not have built-in support for the US Payflow Pro service. However, there is a [free addon](https://www.zen-cart.com/downloads.php?do=file&id=212) which can be used for this purpose if required.  

Please see PayPal's website for more [Payflow and PayPal](https://www.zen-cart.com/partners/paypal) information.  

**PayPal Commerce** is another PayPal offering.  It is not supported at this time by Zen Cart, and adding it is not on the roadmap.

### Where can I learn more about PayPal? 

PayPal provides a series of [Help Guides](https://www.paypal.com/us/smarthelp/PAYPAL_HELP_GUIDE) with information about how to handle common situations. 

More information about the various PayPal services can be found on the [PayPal website.](https://www.zen-cart.com/partners/paypal)  

---
