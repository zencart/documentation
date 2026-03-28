---
title: PayPal RESTful
description: The most-up-to-date PayPal Integration for Zen Cart
category: payment 
weight: 10
---

PayPal RESTful is a new integration with PayPal which uses the [PayPal REST API](https://developer.paypal.com/api/rest/).
It replaces both PayPal Express and PayPal Website Payments Pro ... and also replaces PayPal Standard.  (You may sometimes hear these integrations referred to as the "NVP/SOAP API integrations.")

If you are using one of the older PayPal integrations, migrating to the RESTful module is highly recommended, and is quite straightforward.

{{% paypal_restful_links %}}

![PayPal RESTful](/images/paypal_restful.png)

PayPal RESTful is compatible with both [standard three page checkout](/user/storefront_pages/checkout/) and [one page checkout](/user/running/checkout/).

Storeowners who currently process orders using PayPal Express and/or PayPal Website Payments Pro will want to [retire](/user/payment/retirement/) those modules when they enable PayPal RESTful - having both enabled will be confusing to customers. 

Pay-Later / Pay-in-4 messaging is supported.

At this time, PayPal RESTful does not support Venmo.

