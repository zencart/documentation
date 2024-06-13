---
title: Offline Payment
description: Taking payment outside the checkout flow process 
category: payment
weight: 10 
---

Sometimes it is convenient to offer payment methods where payment does not occur when the order is placed.  Instead, they are dependant on an action which will occur **outside the shopping cart ordering process**.    These are called offline payment methods. 

These payment methods appear on the checkout payment page (or the one page checkout page), but require a second step from your customer before you process and fill the order.  Most Zen Cart storeowners use the "Pending" order status to indicate that this second step has not yet been completed.

Note: The options below are payment modules, which are designed to be used for an order.  If you need additional payment for an order which has already been placed, see [balance owed payments](/user/payment/balance_owed/).

## Check/Money Order

If you offer check/money-order, then it's up to the buyer to send the check to you.  

Naturally, you will typically wait for the check to arrive and clear your bank before shipping the goods.  

This precaution also holds true for Bank Transfer, e-Transfer or Bank Deposit: you wait for payment before fulfilling the order.

The mechanism for doing this in Zen Cart is to set the Order Status for the Check/Money Order module to "Pending."  It should stay in this state until payment is received.  

Note: The Check/Money Order module can be used for *any* payment method where transfer of funds does not take place within the checkout flow.  For example, you can accept payment by Venmo simply by modifying the language defines in in `./includes/languages/english/modules/payment/moneyorder.php`.  

Alternately, you may [clone the moneyorder payment module](/dev/code/modules/clone_payment/) to build a Venmo module with its own rules and behaviors.

## Other Built-In Offline payment methods 

Zen Cart also offers the following built-in offline payment methods:

- Cash On Delivery (COD)

## Plugins for Offline Payment 

Finally, plugins are available for other offline payment methods: 

- [Invoice](https://www.zen-cart.com/downloads.php?do=file&id=131)
- [Zelle](https://www.zen-cart.com/downloads.php?do=file&id=2301)
- [Call In Payment](https://www.zen-cart.com/downloads.php?do=file&id=2388)

