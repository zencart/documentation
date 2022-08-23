---
title: PayPal Express Checkout setup
description: The preferred way to use PayPal in Zen Cart 
category: payment
weight: 10
---

## PayPal Express Checkout

<div style="float:right;width: 155px;padding-left:15px;">

[![PayPal [link]](/images/PayPal_Certified.gif "PayPal [link]")](https://www.zen-cart.com/partners/paypal)

</div>

*   Accept not only credit card payments but also allow PayPal members to pay from their PayPal account.
*   No registration required on your Zen Cart site when using PayPal Express Checkout.
*   Get PayPal's industry-leading security fraud-prevention systems.
*   Take advantage of comprehensive PayPal's online reports that help you measure sales and manage your business easily.

## Configuring Zen Cart to use PayPal Express Checkout 

Here's how to put Zen Cart and Express Checkout to work for your business.

*   **Step 1: [Download and install the latest version of Zen Cart](/user/first_steps/get_zen_cart/)**
*   **Step 2: Set Up a Verified PayPal Business Account**
    *   Customers who don't have an existing PayPal account:
        1.  [**Go to** ![PayPal [link]](/images/paypal.gif "PayPal [link]")](https://www.zen-cart.com/partners/paypal-ec)
        2.  Click Sign Up Today.
        3.  Set up an account for Business Owners.
        4.  Follow the instructions on the PayPal site.
    *   Customers who already have a Personal or Premier account:
        1.  [**Go to** ![PayPal [link]](/images/paypal.gif "PayPal [link]")](https://www.zen-cart.com/partners/paypal-ec)
        2.  Click the Upgrade your Account link.
        3.  Click the Upgrade Now button.
        4.  Choose to upgrade to a Business account and follow instructions to complete the upgrade.
        5.  If you haven't already, add a bank account to become a Verified member. Follow the instructions on the PayPal site. (This process may take 2-3 business days.)
*   **Step 3: Setup API Access**  
    1. Get [your API credentials](https://www.paypal.com/us/cgi-bin/webscr?cmd=_get-api-signature&generic-flow=true).
    2. Click the "Show" link under API Username, API Password and Signature and note all three values.
    3. At the top right hand side of the page, click your account name, then click Account Settings.  Navigate to **Business Information** and note your **Merchant ID**.  It will look like *FDEFDEFDEFDE11*. 
    4. Use the values from the prior step in Admin > Configuration > Payment to configure the PayPal Express fields **API Signature**, **API Signature -- Password**, and **API Signature** and **Merchant ID**. 


## Configuring Zen Cart to accept credit cards directly on your site 

Here's how to add your own merchant account and accept credit cards without sending your customers off-site

Get the features of an internet merchant account and payment gateway with Website Payments Pro. Control your checkout from start to finish by integrating PayPal Website Payments Pro with your Zen Cart shopping cart.

*   **Apply for Website Payments Pro**
    1.  [**Go to** ![PayPal [link]](/images/paypal.gif "PayPal [link]")](https://www.zen-cart.com//partners/paypal-pro)
    2.  Login to your PayPal Business Account
    3.  Click the Merchant Services tab.
    4.  Click Website Payments Pro in left column.
    5.  Click Sign Up
    6.  Fill in your information, and submit your application. Approval takes between 24 and 48 hours.
    7.  Once approved, accept the Pro billing agreement. Check the Getting Started section on the upper left of your account overview page.
    8.  In your Zen Cart admin, enable the Website Payments Pro module and choose the appropriate settings for your account.

