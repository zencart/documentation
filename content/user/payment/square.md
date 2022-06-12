---
title: Square Web Payments API
description: How to collect payments with Square 
category: payment
weight: 10
---

There are two Square modules for Zen Cart: 
- A newer one, based on the Square Web Payments API, which is currently available as the [Square Web Payments API plugin](https://www.zen-cart.com/downloads.php?do=file&id=2345). 
- An older one, based on the Square Payments Form library.  This was built in to Zen Cart from 1.5.5 to 1.5.7.  Please note this library has been deprecated by Square, and the older module will cease to work in July 2022.  The [Square Payments Form documentation](/user/payment/square_payments_form/) is maintained for historical purposes. 

## Newer Module - Square Web Payments API 
The newer Square module is available in the Plugins library as [Square Web Payments API plugin](https://www.zen-cart.com/downloads.php?do=file&id=2345). 

![Square Modules](/images/square_payment_modules.png)
- The top one is the old Square module.
- The bottom one is the new Square module.

## Requirements
1. You must be using SSL on your website
1. You will need a Square account, already validated and connected with your bank. You may [create a Square merchant account here](https://squareup.com/t/f_partnerships/d_partnerpage/p_zencart/c_general/o_free_processing/u_signup/l_us?route=signup%3Fsignup_token%3D6BB5B2E676)

Please note: do NOT remove the old Square files from your Zen Cart installation.  Cleanup of old files will be done in the next release. 

## Installing Square Web Payments - first time 
1. Install the Square Web Payments module files.  Then to go to Admin > Modules > Payments > Square WebPay, and click **Install**. 
1. Login at [https://connect.squareup.com/apps](https://connect.squareup.com/apps) to view the apps you've connected to your account.
1. Click **+** to create a New Application for your Zen Cart store. Give it a name, such as "WebPay", and click **Save**.
1. Click on the application icon that was just created (named "WebPay" or whatever name you used).
1. The environment will be Sandbox by default.  Click "Production".
1. Copy and Paste the Production Application ID into your Square WebPay configuration in Zen Cart admin. 
1. Click on the OAuth tab. In the "Redirect URL" field, enter `https://YOURSTORE.com/squareWebPay_handler.php` and click **Save** at the bottom. (Ensure the URL you enter points to the correct directory or subdirectory on your server.)
1. Now click **Show** on the Production Application secret field.  Copy and Paste the secret into your Square WebPay configuration in Zen Cart admin.
1. In your Zen Cart admin, do the following: 
  - Click **Update** to save the new Square WebPay config values. 
  - Click the green button in the Zen Cart admin sidebar that says "Click here to login and Authorize your account."  If everything is correct, the Sort Order LED for Square WebPay will go green. 
  - Click the **Edit** button one more time.  This will fill in the Location ID field.  Click **Update**. 


## Upgrading to Square Web Payments from Square Payments Form 

1. Go to Admin > Modules > Payment > Square, click **Edit**, and set Enable Square Module to false, then click **Update**.
1. Login at [https://connect.squareup.com/apps](https://connect.squareup.com/apps) and rename your existing Square app to something like "OLD Webstore".
1. Use the Installation instructions above. 
1. Once you are certain Square Web Payments is working, Go to Admin > Modules > Payment > Square and click **Remove**. 

