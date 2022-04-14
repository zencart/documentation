---
title: Authorize.net AIM Payment Module
description: Zen Cart Authorize.net AIM Payment Module
category: payment
weight: 10
---

## REQUIREMENTS

*   Authorize.net Account [Support Zen Cart by Clicking Here to Sign Up for an Account now](https://account.authorize.net/ui/themes/anet/oauth/PricingPage.aspx?resellerId=10023)
*   CURL is required and MUST be compiled into PHP with TLS/SSL support  

*   Your Username and Transaction key (generated in your authorize.net account area)
*   You need to have HTTPS/SSL active on your site to protect your customers' sensitive data  

## INITIAL SETUP

You need to generate your username and transaction key:  

1.  Log in to your Authorize.net account on the authorize.net website.  

2.  Click on "Account" in the Main Menu Bar.
3.  Click on the "API Login ID and Transaction Key" link under Security settings.
4.  Your username will be shown. Record it.  

5.  To generate a new Transaction Key (which is required for new accounts, and also recommended if switching from test mode to production mode), fill in the answer to the security question, and check the box to disable the old key.
6.  Copy and paste your Transaction Key into your Zen Cart settings.

## CONFIGURING THE MODULE

1.  Login to your Zen Cart Admin
2.  Go to Modules
3.  Go to Payment
4.  Select Authorize.net AIM and click Install
5.  Enter your Login ID and Transaction Key as recorded earlier
6.  Configure the rest of the settings as desired:

1.  Transaction Mode Response -- Set this to Production for normal use, or simulate some tests using the Test option (See below for testing instructions). **NOTE:** This can be set to "Test" or "Production" regardless of whether your Authorize.net account is in Test mode.  

2.  Authorization Type - In most cases you will want to do an "Authorize+Capture" to capture payment immediately. In some situations, you may prefer to simply "Authorize" transactions, and then manually use your Merchant Terminal to formally capture the payments (esp if payment amounts may fluctuate between placing the order and shipping it)
3.  Enable Database Storage - If you enable this option, extended details of each transaction will be stored, enabling you to more effectively conduct audits of fraudulent activity or even track/match order information between Zen Cart and your Authorize.net records.
4.  Customer Notifications - If enabled, Authorize.net will email a basic receipt to your customers when activity occurs on their card as a result of anything related to transactions you process for them, including purchases as well as refunds.
5.  Merchant Notifications - If enabled, you will also get the emails mentioned above.
6.  Request CVV Number - If enabled, this will cause the customer to be asked for their 3-or-4 digit number off the back of their card. This is important for card validation, and should usually be enabled.
7.  Sort Order of Display -- Any value greater than zero will cause this payment method to appear in the specified sort order on the checkout-payment page
8.  Payment Zone - if you want only customers from a particular zone to be able to use this payment module, select that zone here.
9.  Set Completed Order Status - For Captured and Approved orders, what order-status should be set?  Default recommended is "Processing"
10.  Set Refunded Order Status - For transactions that are refunded, this order status setting will be used. Recommended: "Pending"
11.  Debug Mode - If you need to diagnose what details are sent to and received from the Authorize.net gateway, enable this option. Logs will be stored in the /cache folder and numbered in obscurity to prevent snooping. Set it to "Alerts Only" if you want to be emailed if payment system errors occur but not clutter log folders on the server.  

## TESTING

You'll probably find that even for testing you'll need to have an SSL certificate on your store. Transactions may be rejected if not submitted over SSL.  

To test your shop, 

- Set your  Authorize.net Transaction Mode to "Test".  You DO NOT need to have your actual account in Testing mode; this will simulate a test even against a Production account.
- Run a transaction in your shop.   
- Once satisfied, set the Transaction Mode to 'Production'  

========================================================  

## TRANSACTION DATA SHOWN IN ZEN CART  

1\. Incorporated with each successful order is a listing of:  
*Authorize.net generated Order ID  
*Approval Code  
*Reference Number  
*AVS Response  
*Fraud Score  
*Response Message  

The first 3 values should help you cross reference your orders to the Authorize.net system.   
The 4th value AVS (Address Verification System) should help you determine fraud or not.
