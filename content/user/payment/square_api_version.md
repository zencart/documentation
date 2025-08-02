---
title: Square API Version
description: Setting and changing the API version for Square 
category: payment
weight: 10
---

This content applies to [Square Webpay](/user/payment/square/) only.

**Please note the specific versions below are examples only - the current version may use different dates.  Be sure to get the correct API version for your copy of Square WebPayments.**

For versions 3.x and above, the Square API version is set in the file 
`includes/modules/payment/square_webPay/square/square/src/Legacy/ConfigurationDefaults.php`

It looks like this:
```
    public const SQUARE_VERSION = '2025-01-23';
``` 

For versions 2.x and below, the Square API version is set in the file 
`includes/modules/payment/square_webPay/square/square/src/ConfigurationDefaults.php`

It looks like this:
```
    public const SQUARE_VERSION = '2024-01-18';
``` 


Be sure to specify the correct version on the Credentials page for your App when you first install Square Webpay, and every time you update the Square Webpay software.  To change the version for your site, go to https://connect.squareup.com/apps, select your app, then click "App details" on the left sidebar.  

![Square App Details](/images/square_app_details.png)

Click the "Change version" link on the "Production API version" line.

![Square API Version](/images/square_change_api_version.png)

Set it to the version in the file shown above.  

You may use different API Versions for your live and test sites by creating both a live and a test app, and setting the versions on each independently.  This can be convenient in situations like testing an upgrade. 

