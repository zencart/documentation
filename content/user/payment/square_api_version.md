---
title: Square API Version
description: Setting and changing the API version for Square 
category: payment
weight: 10
---

This content applies to [Square Webpay](/user/payment/square/) only.

**Please note the specific versions below are examples only - the current versions use different dates.  Be sure to get the correct API version for your copy of Square WebPayments.**

Your API version is set in the file 
`includes/modules/payment/square_webPay/square/square/src/ConfigurationDefaults.php`

It looks like this:
```
    public const SQUARE_VERSION = '2024-01-18';
``` 

Be sure to specify the correct version on the Credentials page for your App when you first install Square Webpay, and every time you update the Square Webpay software.  To change the version, go to https://connect.squareup.com/apps, select your app and click the "Change version" button under the "API version" heading.

![Square API Version](/images/square_api_version.png)

To change the API version, go to https://connect.squareup.com/apps and click on the app you want to update (remembering that the live and the test app, if one exists, will be separate).

Then, under the heading API Version, click the Change Version button. Set it to the version in the file shown above.  

You may use different API Versions for Sandbox vs Production (again assuming you have both a live and a test app).  This can be convenient in situations like testing an upgrade. 

