---
title: Credit Card Authorize vs Capture
description:  How do I authorize a Credit Card but not actually charge it until I ship the goods?
category: payment
weight: 10
---

While many businesses will want to take payment immediately online, sometimes the business model requires that the customer's card be authorized but **not charged** until the goods have been shipped.

Most gateways allow your customers to authorize the payment but not actually pay.  You would then capture the payment when you actually ship the goods.  This must be done within a limited time window.  Also, typically you can only capture (up to) the amount authorized, although some gateways will give you a small amount of wiggle room.  

- For PayPal, the authorization window is 29 days, and the captured amount may be up to 115% of the authorized amount.
- For Square, the authorization window is 7 days, and the captured amount may be up to 100% of the authorized amount.

If additional funds need to be captured beyond what is allowed, see [balanced owed payments](/user/payment/balance_owed/). 


## Authorize-Only
To enable this, check whether your module has an option to specify `Authorize-Only` mode, and enable it. (As opposed to `Charge` or `Capture` mode.)

The process is this:
1. Customer places an order. The card is only `authorized`.
2. Prepare the order
3. Log in to your Merchant Gateway system. Find the transaction for that customer/order.
4. Choose the option to `Capture` the funds. This charges the card and puts the money in your bank account during the next settlement/processing batch.
5. Ship the goods

If you set your payment module to Authorize-Only, be sure to set the [Order Status](/user/localization/orders_status/) to Pending, just like an [offline payment module](/user/payment/offline/). 

## Authorize And Capture Immediately
The process is this:
1. Customer places an order and submits for payment. The card is authorized and funds captured immediately.
2. You fulfill the order by shipping the goods (or customer gets immediate access to their downloads).
