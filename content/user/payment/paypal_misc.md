---
title: PayPal - Miscellaneous Questions
category: payment 
weight: 10
---

{{< misc >}} 

---
### Where can I learn more about PayPal? 

PayPal provides a series of [Help Guides](https://www.paypal.com/us/smarthelp/PAYPAL_HELP_GUIDE) with information about how to handle common situations. 

---

### How do I set up PayPal Standard to return to my store automatically?

Detailed setup instructions for **PayPal Standard** can be found [in this article](/user/payment/paypal/).

The quick overview for properly configuring IPN is as follows:  
1\. You must have a "Premier" or "Business" PayPal account in order to use the PayPal module for receiving payments.  

2\. Log into your PayPal account and go to the "Profile" tab.  

3\. Click on "Website Payments Preferences"  

4\. Change Auto-Return to "On"  

5\. Provide return URL: `https://www.YOURSITE.com/index.php?main_page=checkout_process`

6\. Also on the same screen, lower down: PayPal Account Optional - your choice. If you set this to "On", then people who do not have a PayPal account can still pay via their credit card through the PayPal site, without having to create a PayPal account (although they'll be encouraged to create one).

**Note: The sessions work automatically. Do not change your sessions setting in the Zen Cart Admin.**

---
### PayPal login screen vs Credit Card fields ... using PayPal Website Payments Standard

#### Question: 

When I'm testing payments on my shop using PayPal Website Payments Standard, it takes me to a screen where I'm asked to login to my PayPal account. But, I don't want my customers to be asked to login. I want them to see clearly that they can pay via Credit Card instead of having to locate the tiny text link that says "continue to pay by credit card".  How can I change this?  

#### Answer:

When you login to PayPal, it sets a cookie in your browser. Then the next time you are taken to PayPal to make a payment for a purchase, it presents you with only the login screen (and the small Continue link). This is to make it more convenient for you the next time you go to use your PayPal account.  

However, if you've never visited PayPal, or if you've cleared your browser's cache and cookies, you'll see the "split screen", where both CC and PP-login options are presented on the same screen.  

**So, all in all, your customers will see what makes sense based on their shopping experiences. If they don't have a PayPal account, they will see the "split screen" automatically.**  

If you need more proof, try clearing your browser's cache and cookies. Or, try a different browser/computer where nobody's ever logged in to PayPal from it.  

---
### How do customers use PayPal to pay with their Credit Card?

When customers transfer from your site to the PayPal website, they are presented with a screen showing some of the details of their purchase.
They are also given some fields in which to enter their PayPal username and password if they wish to pay using their PayPal funds.

Underneath the PayPal username/password fields is a text link to click: "Don't have a PayPal account? Click here" ... which takes them to a screen where they can fill in their details and use a Credit Card to pay. (They can still log in to their PayPal account from that screen too.)  They are not required to create a PayPal account. 

One of PayPal's quirks is that they can only use an address and credit card from the same country as what they used in Zen Cart when they created their account. This is usually not a problem.

Additional information on limitations imposed by PayPal regarding payment without an account can be found below.

---
### Why can't my customers pay without having a PayPal account?

#### The Situation

My store is set up to use **PayPal Payments Standard** to receive payments from customers.  
I want to allow my customers to pay via Credit Card without having to create a PayPal account.  
However, some customers are not given this option, and are required to create a PayPal account before they can complete a checkout.  

#### Cause/Solution

1.  PayPal has an "Account Optional" setting in your PayPal account Profile, under Payment Receiving Preferences.  Ensure that it is on.
2.  However, note that the PayPal account optional is not available for all locations, some locations (or countries, including China) are required by PayPal to have a PayPal account before making a transaction. In this same regard, if the IP address of the buyer is determined by the system to be at a location where the PayPal account optional is not available, they will be required to create a PayPal account.

#### Comments

*   Note that the **PayPal Express Checkout** product technically does not allow the option to make payment without having a PayPal account (although many Zen Cart sites do have success with this option due to special concessions granted by PayPal to the Zen Cart software). PayPal has always intended that Express Checkout be offered in addition to other payment choices such as a credit card gateway, and that adding Express is a way to allow PayPal members a very quick and easy way to pay using their PayPal account.  

*   The **PayPal Payments Pro** product (which you must pay a monthly fee to PayPal to use, and is only available to US, UK, and Canadian merchants) adds the ability to accept Credit Card payments directly on your website without the customer even knowing that they are being processed by PayPal.  [Contact your PayPal representative for information](https://www.zen-cart.com/partners/paypal) and to sign up for this service.

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
<!-- please keep this at the end --> 
{{< faq_questions >}}
