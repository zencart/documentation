---
title: Credit Card Authorize vs Capture
description:  How do I authorize a Credit Card but not actually charge it until I ship the goods?
category: payment
weight: 10
---

While many businesses will want to take payment immediately online, sometimes the business model requires that the customer's card be authorized but **not charged** until the goods have been shipped.

Most gateways allow you to `authorize only` for the payment, and then within a week `capture` the payment when you ship the goods. 
The length of time allowed before `capture` depends on the contract you have with the Gateway (based on their rules, and on the kind of business you run).

## Authorize-Only
To enable this, check whether your module has an option to specify `Authorize-Only` mode, and enable it. (As opposed to `Charge` or `Capture` mode.)

The process is this:
1. Customer places an order. The card is only `authorized`.
2. Prepare the order
3. Log in to your Merchant Gateway system. Find the transaction for that customer/order.
4. Choose the option to `Capture` the funds. This charges the card and puts the money in your bank account during the next settlement/processing batch.
5. Ship the goods

## Authorize And Capture Immediately
The process is this:
1. Customer places an order and submits for payment. The card is authorized and funds captured immediately.
2. You fulfill the order by shipping the goods. (Or customer gets immediate access to their downloads.)
