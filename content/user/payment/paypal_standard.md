---
title: PayPal Standard - Potential Problems 
description: Why you shouldn't use PayPal Standard with Zen Cart 
category: payment
weight: 10
---

Symptom: 

- Duplicate transactions 
- Missing transactions 

Root Cause: using PayPal Standard instead of PayPal Express. 

This is a common problem typical to using the PayPal Standard module, since it relies on ancient technology that was based on putting your products into PayPal, having people create a checkout basket on PayPal, submitting payments to buy those things, and then telling "your site" that a sale had occurred so you could fulfill orders. It was the first variant of PayPal payment processing, and was never (and still isn't) intended for online stores with their own catalogs and product management.

Standard doesn't give the store real-time verification that the payment has been completed. In fact, if the customer doesn't properly return to the store (clicking the Return button after payment is complete) and closes their browser, then no order will be stored at all, nor any confirmation email.

Instead, it posts an IPN "Instant Payment Notification" to the store, via the ipn_main_handler.php file which then attempts to re-instantiate the customer's session via very complex and fragile means, verify the incoming IPN is actually relevant to a current transaction (and not a spoof), and then stores the order, completes the sale, and sends the confirmation email. All out-of-band.
If IPN acknowledgements aren't responded to automatically then PayPal attempts the IPN again multiple times.

A PDT process attempts to do a payment verification "in-band" if the customer actually clicks to return to the store. This basically does the whole IPN thing as well. Hopefully before the IPN is actually sent from PayPal. This allows the order to be saved almost in-real-time, so the customer gets notification and a completed order while they're still on the checkout-success page.

There's a small possibility of a race-condition where the customer clicks the Return link at the same instant that PayPal sends the IPN, and both the PDT and IPN processes which are searching for the customer's account and session and inspecting the order don't discover that the other is already doing its thing, and thus each creates a sale, resulting in duplicates.

Further, if the IPN feature isn't turned on in the account, or if IPNs aren't acknowledged by the store for a period of time, PayPal will disable the feature on the account, meaning purchases made will never turn into actual orders in the store.

All this out-of-band, non-real-time stuff makes it rather unreliable (or unpredictable) and is exactly the reason why using PayPal Standard is not recommended. It purpose for still being in core code is (was) to support countries that can't (couldn't) offer Express Checkout while PayPal was still rolling it out around the world.



