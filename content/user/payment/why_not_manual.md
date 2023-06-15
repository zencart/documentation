---
title: Manual Credit Card Collection - Potential Problems 
description: Why you shouldn't use manual credit card processing with online stores
category: payment
weight: 10
---

Older payment modules like `credit card` and `CEON Manual Card` are not recommended for the following reasons: 

- they are not PCI Compliant
- storing credit card details in your database puts the store owner at great financial risk in the event of a data breach.  [Fines can range from $5000 to $500,000 for said breach.](https://ebizcharge.com/blog/storing-credit-card-information-safely-in-2022-the-dos-and-donts/#:~:text=In%20addition%2C%20if%20a%20merchant,far%20outweighs%20any%20security%20solution.)
- it may no longer be legal to do this (depending on your jurisdiction)
- it may be a violation of your merchant agreement (depending on the terms you agreed to).

So what should you do? 

- Switch to one of the built-in payment gateways.  There are many [payment processors Zen Cart supports](https://www.zen-cart.com/content.php?14-Payment-Processing). 

- Switch to one of the [payment gateways from the Plugins Library](https://www.zen-cart.com/downloads.php?do=cat&id=8).

The former will be better supported of course, but it's your choice.

Notes: 

- Many gateways can be configured to [Auth Only instead of Auth and Capture](/user/payment/auth_only/) if your concern is that the final order total might change.

- The plugin [Authorize.net CIM Card on file](https://www.zen-cart.com/downloads.php?do=file&id=2272) allows you to securely store credit card information at the payment gateway.  The Zen Cart database stores only a token for use in future charges.  This method of tokenizing credit card data is the accepted best practice for enacting card on file transactions.

All these options give you a credit card entry form on your checkout payment page, which is what most customers will expect.  (Naturally they all require an [SSL certificate](/user/security/ssl_cert/), but hopefully you already have one; if not, [install SSL](/user/installing/enable_ssl/) first.)

