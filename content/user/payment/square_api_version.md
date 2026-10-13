---
title: Square API Version
description: Setting and changing the API version for Square 
category: payment
weight: 10
---

This content applies to [Square Webpay](/user/payment/square/) only.

**Please note the specific versions below are examples only - the current version may use different dates.  Be sure to get the correct API version for your copy of Square WebPayments.**

The API version in use is shown in Admin > Modules > Payment > Square WebPay at the top of the screen.  It looks like this: 

![Square API Version in Zen Admin](/images/square_api_version_zc.png)

<br>

This means the version you will want to specify in the Square app (see below) is "2026-01-22"

Be sure to specify the correct version on the Credentials page for your Square App (in connect.squareup.com) when you first install Square Webpay, and every time you update the Square Webpay software.  To change the version for your site, go to https://connect.squareup.com/apps, select your app, then click "App details" on the left sidebar.  

![Square App Details](/images/square_app_details.png)

Click the "Change version" link on the "Production API version" line.

![Square API Version](/images/square_change_api_version.png)

Set it to the version in the file shown above.  

You may use different API Versions for your live and test sites by creating both a live and a test app, and setting the versions on each independently.  This can be convenient in situations like testing an upgrade. 

