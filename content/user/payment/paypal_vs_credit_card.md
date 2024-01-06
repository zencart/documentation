---
title: PayPal Paying with Credit Card vs a PayPal Account
description: Customer questions regarding PayPal
category: payment 
weight: 10
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

*   UPDATE: PayPal has now stated that they will permit PayPal Express Checkout Business customers to not require that customers have a PayPal account.  In your PayPal account, click on your account name at the top right, then click Account Settings, and navigate to the Website Payments section, then look for PayPal account optional.  You want this to be **On**.  Also, in your Zen Cart PayPal Express configuration, you want the *Use InContext Checkout?* setting to be **Old**.

![PayPal Account Optional](/images/paypal_account_optional.png)

*   The **PayPal Payments Pro** product (which you must pay a monthly fee to PayPal to use, and is only available to US, UK, and Canadian merchants) adds the ability to accept Credit Card payments directly on your website without the customer even knowing that they are being processed by PayPal.  [Contact your PayPal representative for information](https://www.zen-cart.com/partners/paypal) and to sign up for this service.


--- 
