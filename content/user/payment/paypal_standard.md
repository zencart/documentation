---
title: PayPal Standard - Potential Problems 
description: Why you shouldn't use PayPal Standard 
category: payment
weight: 10
---

### Why not to use Payments Standard

If possible, avoid using PayPal Payments Standard. Here's why ...

Symptom: 

- Duplicate transactions 
- Missing transactions 

Root Cause: using PayPal Standard instead of PayPal Express. 

This is a common problem when using the PayPal Standard module.  The problem is that PayPal Standard relies on ancient technology that was based on a workflow that predates true e-commerce: 

- putting your products into PayPal 
- having people create a checkout basket on PayPal 
- submitting payments to buy those things, and then 
- telling "your site" that a sale had occurred so you could fulfill orders. 

It was the first variant of PayPal payment processing, and was never (and still isn't) intended for online stores with their own catalogs and product/order management.

Standard doesn't give the store real-time verification that the payment has been completed. In fact, if the customer doesn't properly return to the store (clicking the Return button after payment is complete) and closes their browser, then no order will be stored at all, nor will a confirmation email be sent.

Instead, Standard posts an IPN ("Instant Payment Notification") to the store, via the ipn_main_handler.php file, which then attempts to re-instantiate the customer's session via very complex and fragile means, verify the incoming IPN is actually relevant to a current transaction (and not a spoof), and then stores the order, completes the sale, and sends the confirmation email. All out-of-band.
If IPN acknowledgements aren't responded to automatically then PayPal attempts the IPN again multiple times.

A PDT ("Payment Data Transfer") process attempts to do a payment verification "in-band" if the customer actually clicks to return to the store. This basically does the whole IPN thing as well. Hopefully before the IPN is actually sent from PayPal. This allows the order to be saved almost in-real-time, so the customer gets notification and a completed order while they're still on the checkout-success page.

There's a small possibility of a race-condition where the customer clicks the Return link at the same instant that PayPal sends the IPN, and both the PDT and IPN processes which are searching for the customer's account and session and inspecting the order don't discover that the other is already doing its thing, and thus each creates a sale, resulting in duplicates.

Further, if the IPN feature isn't turned on in the account, or if IPNs aren't acknowledged by the store for a period of time, PayPal will disable the feature on the account, meaning purchases made will never turn into actual orders in the store.

All of this makes PayPal Standard unreliable, and is exactly the reason why it is not recommended.  The only reason it is still part of Zen Cart is that some less-developed countries can't offer Express Checkout.  Unless this is an issue for you, you should be using PayPal Express.

[Read about installing PayPal Express](/user/payment/paypal_express_checkout/). 


#### Using Payments Standard Anyway

AGAIN: You should NOT be using Payments Standard; you should be using Express Checkout which is far more reliable.

But, if you insist on using the older technology of Website Payments Standard, follow these instructions:

Important: If you're reading this far then you've ignored the important notices above: You should be using Express Checkout instead of Payments Standard. Seriously.

Now, re-read the sentence above.

And once again.

If you're truly choosing to ignore the important advice to use Express Checkout instead, the following settings are required to use Payments Standard:

**ON THE PAYPAL WEBSITE**

1.  Log in.
2.  Click on _Profile_.
3.  Click on _Email_.
4.  Write down your _primary_ email address. You need to use this exact email address in your Zen Cart settings in the next section below.
5.  Click on Profile again.
6.  Click on Instant Payment Notification Preferences.
7.  Click on Edit.
8.  Turn it on (check the box).
9.  Set the URL to: `https://www.YOURSTORE.com/ipn_main_handler.php`. (The complete correct URL can be obtained from your Admin area inside the PayPal payment module's information settings.)
10.  Click Save.
11.  Click on Profile.
12.  Click on My selling tools.
13.  Click on Website Payment Preferences.
14.  Auto Return for Website Payments - set to on.

Provide the Return URL (obtain correct URL from your Zen Cart admin.  It will take the form of something like the following examples): `https://www.YOURSTORE.com/index.php?main_page=checkout_process`

15.  Other settings in this area can be set based on your preferences. Consult PayPal for their meanings.

  `My selling tools > Website Preferences > Payment Data Transfer`: If you're using PDT, make sure you have the same token in Zen Cart as you have in PayPal.

  `Encrypted Website Payments`: Set this to OFF. Zen Cart does not currently support this option.

  `PayPal Account Optional`: if you want to allow customers to pay by credit card and not have to create a PayPal account, set this to ON

16.  Click _Save_.
17.  If your website's language is not a Western/European language, go to Language Encoding and set your language.
18.  **Turn off ALL tax and shipping settings in your PayPal account**. These will cause your transaction amounts to not match Zen Cart amounts, and thus your orders will not be released.

**Note:** if you've never had your PayPal account "verified", you should follow their steps to do so.

**IN ZEN CART**

1.  Go to Admin > Modules > Payment > PayPal
2.  If this is the first time configuring for PayPal on this site, then you need to click on _Install_.
3.  Otherwise, click on _Edit_.
4.  Enter the primary email address of your PayPal account.
5.  Configure any other options as desired.
6.  Note the URL's suggested in the top of the PayPal module's instructions - they should match what you have set in your PayPal profile in the steps above for the PayPal site.


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


### How Payments Standard IPN works

"IPN" means "Instant Payment Notification." It's part of PayPal's "Website Payments Standard" service.

1.  Customer places an order on your site
2.  For payment, they are taken to a link on PayPal's site, where they provide their information and pay for their order.
3.  They click a link when finished (or wait 5 seconds) and return to your site.

Meanwhile, between steps 2 and 3 above, PayPal's server does this:

1.  PayPal's server sends a request to your website, which is waiting and listening for connections from PayPal to the `ipn_main_handler.php` page.
2.  Your server sits waiting and listening for hits to `ipn_handler.php`.
3.  When your server receives a request, it attempts to validate and be sure that the PayPal data provided matches the order details for which it is intended.
4.  If validation passes, the customer's order is released, and it lets the PayPal server know that you received their confirmation. This handshaking happens via CURL on port 443, and requires that your server be configured for modern TLS communication to https URLs.
5.  **NOTE:** PayPal's server will attempt the IPN notification (hourly) for up to four days if it's not successful on the first try. In this case your customer's order will not show up in your Admin until the IPN notification is successful.


### Things to check if Payments Standard is not working

These are the common mistakes causing Website Payments Standard transactions to fail:

1.  Check that the email address you enter for PayPal in Zen Cart admin matches case-sensitive exactly with your PRIMARY email address setting in your PayPal account profile on PayPal's site.
2.  Is your PayPal account "verified" yet?
3.  Is your PayPal account a "Business" account? (Business is preferred. Premier can be used in some cases (Ask your PayPal rep if unsure). Personal cannot.)
4.  Check your PayPal profile's **Website Payment Preferences** settings on [paypal.com](https://paypal.com/):

  - Your Return URL should be set to your site's checkout_process page. (ie: `https://www.YOURSITE.com/index.php?main_page=checkout_process`).
  - It is advisable to have Auto Return set to On.

5.  **Turn off ALL tax and shipping fees in your PayPal profile**. They will cause the purchase price to mismatch when returning to Zen Cart.
6.  NOW, **also check the [PayPal IPN Troubleshooting](/user/payment/paypal_ipn/) guidance** as well
