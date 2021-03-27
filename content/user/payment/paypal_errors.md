---
title: PayPal Error Messages
description: Understanding the various PayPal errors
category: payment
weight: 10
---

Here are some common PayPal errors and the steps required to fix them. 

--- 

### We cannot process your payment at this time. Please retry your purchase (PayPal)

**Situation:**  
Customer is attempting to complete a purchase and paying via PayPal. They login, provide payment details, and click the Pay Now or Continue button, and they are greeted with the following message and taken back to the PayPal login page, and no details are recorded in your store:  

![Paypal Error - fraud](/images/ppfmferror.jpg)  

**The Reason:** You have your PayPal account configured to use Fraud Management Filters, and the customer's transaction has triggered one of your rules which you've configured for a "Deny" response.  

**Action to Resolve:** You will have to review your PayPal Fraud Management Filters to remove the restriction you've imposed which is causing the customer's transaction to be declined.  

You can access your Fraud Management Filters settings by logging in to your PayPal merchant Account, clicking on "Profile", and choosing "Fraud Management Filters" (or "Risk Controls" if your account is an older account).

--- 
### The PayPal account in this store is presently misconfigured to use mixed sandbox and live settings. We are unable to complete your transaction. Please notify the store owner so they can correct this problem. (10002)


Your PayPal Express Checkout and/or Website Payments Pro module settings require 4 components to be set correctly in order to talk to PayPal successfully. If any one of them is incorrect, you'll not be able to authenticate and submit transactions:

- API Username
- API Password
- API Signature
- PayPal server: live vs sandbox

Normally you would obtain your API details from your real PayPal account profile, and select the "live" server mode.  THIS IS THE BEST ROUTE.


You can only use "sandbox" option if you get API details from the sandbox site's account profile.  Sandbox should not be necessary in most cases.

For more information see [this PayPal page](https://www.paypal.com/us/smarthelp/article/why-did-i-get-api-error-code-10002-ts1030). 


--- 
### PayPal Error 10001: The transaction could not be loaded

If you are doing transaction testing, this error may appear if you attempt to use the reserved CC number of 4111111111111111

Use a different card number instead. 

For more information see [this PayPal page](https://www.paypal.com/us/smarthelp/article/why-did-i-get-api-error-code-10001-ts1041). 

The same error might appear if you've not yet accepted the WPP agreement in your account (or sandbox account). Login to your PayPal account (or sandbox account) and read the agreement and click to accept the terms.

--- 
### PayPal Error - Geographic Region

**Situation:**

The following error occurs when trying to process a payment through PayPal Express near the final stages.

We are sorry for the inconvenience; however, at the present time we are unable to use PayPal to process orders from the geographic region you selected as your PayPal address. Please continue using normal checkout and select from the available payment methods to complete your order.



**Cause:**

That message appears when the customer has supplied an address that your store doesn't recognize or which is outside the zone-restriction you've applied to that payment module.

When the customer returns from PayPal, their selected address is inserted into their customer record in your store. But if it can't do that insertion because the country doesn't exist in your store, or the state/province/region doesn't match one defined in your store for that country, then the error will also be triggered, because if your store won't accept the address then it has to believe that you've told your store not to accept those addresses. (ie: some people delete several countries from the defaults because they don't want to ship to those, etc).

The most common cause of such a problem is triggered by the storeowner setting a Zone in the payment module instead of leaving it set to --None--. By setting a zone, you are restricting that module to only work with addresses which match that zone definition.

---
