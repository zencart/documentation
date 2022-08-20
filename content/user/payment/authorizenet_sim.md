---
title: Authorize.net SIM Payment Module
description: Zen Cart Authorize.net SIM Payment Module (DEPRECATED)
category: payment
weight: 10
---

<font color="red">
<h1>ALERT: DEPRECATED</h1>
</font>

**NOTE:** Authorize.net has officially retired the SIM method of accepting payment. Some older accounts are still working, but you should not plan on using this module moving forward.  Instead, please see [Authorize.net AIM](/user/payment/authorizenet_aim/).

## REQUIREMENTS

*   Authorize.net Account.   [Support Zen Cart by Clicking Here to Sign Up for an Account now](http://reseller.authorize.net/application.asp?id=131345)
*   Your Username and Transaction key (generated in your authorize.net account area)
*   You need to have HTTPS active on your site  

## INITIAL SETUP

You need to generate your username and transaction key:  

1.  Log in to your Authorize.net account on the authorize.net website.  

2.  Click on "Account" in the Main Menu Bar.
3.  Click on the "API Login ID and Transaction Key" link under Security settings.
4.  Your username will be shown. Record it.  

5.  To generate a new Transaction Key (which is required for new accounts, and also recommended if switching from test mode to production mode), fill in the answer to the security question, and check the box to disable the old key.
6.  Copy and paste the new Transaction Key into your Zen Cart settings.  

7.  You also need to set up a Security Key:

1.  Click on New Signature Key
2.  Copy and paste the generated key into your Zen Cart settings.  

9.  Now set your Response/Receipt URLs, Silent POST URL, and Relay Response to blanks. Click on Settings, and go to each of these sections and make sure all are blank:

1.  **Response/Receipt URLs**  
    - delete ALL urls except the 2 "Default" options.  
    - set the "Default" options to blank.  
    _(These URLs are used to authorize your store to process transactions. Leaving them blank means there are no restrictions. Specifying a URL limits the URLs allowed to make transactions with your account. Contact your Authorize.net account representative or their tech support for further information or assistance with these settings.)_
2.  **Relay Response**  
    - Set the Relay Response URL to  
    `https://YOURSITE.com/index.php?main_page=checkout_process`
    Just then be mindful that you'll need to update this setting if you make any changes to your store URLs later.
3.  **Silent POST URL**  
    - Leave this blank  
    _(You are not sending details of purchases to other sites, so leaving this blank is the appropriate choice.)_

## CONFIGURING THE MODULE

1.  Login to your Zen Cart Admin
2.  Go to Modules 
3.  Go to Payment 
4.  Select **Authorize.net SIM** and click **Install**
5.  Enter your **Login ID** and **Transaction Key** as recorded earlier
6.  Enter your **Security Key**.  

7.  Configure the rest of the settings as desired:

1.  Transaction Mode Response -- Set this to Production for normal use, or simulate some tests using the Test option (See below for testing instructions). **NOTE:** This can be set to "Test" or "Production" regardless of whether your Authorize.net account is in Test mode. **NOTE:** TEST TRANSACTIONS WILL NOT APPEAR IN YOUR MERCHANT ACCOUNT AREA.  

2.  Authorization Type - In most cases you will want to use "Capture" to capture payment immediately. In some situations, you may prefer to simply "Authorize" transactions, and then manually use your Merchant Terminal to formally capture the payments (esp if there will be delays in shipping or if payment amounts may fluctuate between placing the order and shipping it)
3.  Request CVV Number - If enabled, this will cause the customer to be asked for their 3-or-4 digit number off the back of their card. This is important for card validation, and should usually be enabled.
4.  Customer Notifications - If enabled, Authorize.net will email a basic receipt to your customers when activity occurs on their card as a result of anything related to transactions you process for them, including purchases as well as refunds.
5.  Payment Zone - if you want only customers from a particular zone to be able to use this payment module, select that zone here.
6.  Set Order Status - For Captured and Approved orders, what order-status should be set?  Default recommended is "Processing"
7.  Sort Order of Display -- Any value greater than zero will cause this payment method to appear in the specified sort order on the checkout-payment page
8.  Gateway Mode -- if you want to handle collecting card numbers ON your site, then set this to "onsite" and be sure your site has SSL protection on it. It's really better to use the AIM module if you wish to do "onsite" card handling.   If you wish to NOT collect credit card numbers on the pages of your site, then set this to "offsite" so customers will be taken to the Authorize.net website to supply their credit card numbers before being returned back to your site to see their order completion details. **NOTE:** Using "offsite" can create abandonments since customers are suddenly taken to some OTHER site to enter their payment details. You might want to configure the appearance of that payment page by editing the appropriate settings in your Merchant Account Settings on the Authorize.net website.
9.  Enable Database Storage - If you enable this option, extended details of each transaction will be stored, enabling you to more effectively conduct audits of fraudulent activity or even track/match order information between Zen Cart and your Authorize.net records.
10.  Debug Mode - If you need to diagnose what details are sent to and received from the Authorize.net gateway, enable this option. Logs will be stored in the /cache folder and numbered in obscurity to prevent snooping. If not debugging specific problems, it's recommended to set it to "Alerts Only" so you'll be notified only if problems occur.  

## TESTING

To test your shop, 

- Set your  Authorize.net Transaction Mode to "Test". You DO NOT need to have your actual account in Testing mode; this will simulate a test even against a Production account.  
- Run a transaction in your shop.   
- Once satisfied, set the Transaction Mode to 'Production'  

