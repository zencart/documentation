---
title: Manual Credit Card Collection - Migrating Away 
description: Getting off manual card collection
category: payment
weight: 10
---

Older payment modules like `credit card` (`cc.php`) and `CEON Manual Card` (`ceon_manual_card.php`) collect and store credit card details on your server.  This is not permitted by PCI rules, and  significant fines are being levied for non-compliance.  Using non-compliant modules like this may be a violation of your terms of service agreement with your hosting company as well.
See [Manual Credit Card Collection](/user/payment/why_not_manual/) for more details if needed. 


## Recommendation 1: Switch to PayPal 

If you have sufficient volume, PayPal will allow you to use PayPal Pro, which has a card entry dialog that will be familiar to any users of manual card collection.  If you don't, you can still use PayPal Express, which completely shields you from card information. 

Documentation: 
- [PayPal Overview](/user/payment/paypal_overview/)

## Recommendation 2: Switch to a payment gateway 

Both Authorize.NET and Square WebPay are well supported options for Zen Cart.  

Documentation: 
- [Authorize.Net CIM](/user/payment/authorizenet_cim/)
- [Authorize.Net AIM](/user/payment/authorizenet_aim/)
- [Square](/user/payment/square/)


## Recommendation 3: Use Auth-Only with your Payment Method

Some businesses with see big variances between the initial order and what is ultimately fulfilled.   The reasons for this are varied: 

- High turnover or supply chain issues, resulting in out of stock conditions
- Products with unusual configurations leading to hidden requirements 
- Customer confusion when presented with multiple seemingly-similar products
- and so on.

For businesses in this situation, it might be preferable to use [Auth Only](/user/payment/auth_only/) rather than Auth and Capture. 

The [PayPal RESTful](https://github.com/lat9/paypalr/wiki/Admin-Handling) documentation provides some good examples of using an Auth Only then later Capture process for orders.

### Dealing with Balance Owed amounts 

Auth Only then capture works well if the order size is reduced, and some payment gateways will even allow a small increase in the capture amount (PayPal supports up to 15%, for example).  But what if the balance owed becomes significant?

Options for collecting these payments are discussed in [balance owed payments](/user/payment/balance_owed/).

## Recommendation 4: Using Offline Payment methods 

If you have a modest order volume, processing payments offline might work for you.  See [offline payment methods](/user/payment/offline/) for ideas. 


