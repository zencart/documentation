---
title: How do I get paid? 
description: Understanding payment collection for your orders 
category: payment
weight: 5
---

Collecting payment from customers requires a means for extracting funds from the payment method the customer chooses.  

## Check/Money Order

If you offer check/money-order, then it's up to them to send the check to you.  

Naturally, you will typically wait for the check to arrive and clear your bank before shipping the goods.  

This precaution also holds true for Bank Transfer, e-Transfer or Bank Deposit: you wait for payment before fulfilling the order.

Note: The Check/Money Order module can be used for *any* payment method where transfer of funds does not take place within the checkout flow.  For example, you can accept payment by Zelle or Venmo simply by modifying the language defines in in `./includes/languages/english/modules/payment/moneyorder.php`.  

Alternately, you may [clone the moneyorder payment module](/dev/code/modules/clone_payment/) to build a Venmo module with its own rules and behaviors.

## Credit Card

_**Before you can accept credit cards directly you must have a merchant account with a Credit Card processing company such as Square, Stripe or Authorize.net.**_

If you offer to let your customers pay by Credit Card, there are several ways to do this:  

a) An online service such as [PayPal](https://www.zen-cart.com/partners/paypal) where the customer makes their payment to the online service, and then that online service sends the money to you via your account with them. A service charge will be levied for each transaction.  

b) Credit Card Gateway service. 
In this case, your customer enters their credit card information directly onto your website (or secure forms that are loaded by your website during checkout). 
Your store then transmits that information securely to a credit-card-processing company's "gateway" to authorize the card/purchase while the customer waits.
If successful, the order is placed, and money is collected from the cardholder's account, and forwarded to your business bank account according to a prescribed schedule.
If it fails, the customer is notified to try again with correct information, thus preventing the use of invalid cards.  

To use this option, you need a business bank account, a merchant account, and a gateway service provider account, all of which incur monthly fees. You can find [recommended payment gateway providers here](https://www.zen-cart.com/content.php?14-Payment-Processing). 

c) Manual processing via a retail/POS terminal or an online virtual terminal.  
In this case, you collect the CC details from the customer and then manually process the card through the terminal provided to you by your merchant bank (usually online). You will require a business bank account and a merchant account; both have monthly and per-transaction fees. 

**Warning**: [online manual card collection is no longer a good option](/user/payment/why_not_manual/).  It is not a secure method for making transactions with an online store, and as such is frowned upon by credit card companies. You really should be using a gateway service as described above. 

### Definitions

**_merchant account_** -- this is a credit/debit-card "processing" account that you arrange with a clearing house, typically your bank.  Its sole purpose is to take the funds collected from credit/debit cards and forward them to the bank account you've arranged for that purpose.  

**_gateway_** -- this is a computer-driven processing system that talks to the credit-card clearing house computers in the national banking system and determines whether a card is valid or not, and allows collection of funds via your merchant account configuration  

**_ISO_** -- this acronym stands for **Independent Sales Organization** (also called a _Member Service Provider_ or _MSP_).  An ISO is a third-party company that is contracted by a credit card member bank to procure new merchant relationships.  Some Zen Cart users get their merchant accounts through an ISO.

### How do I get started?

First, you must realize that Merchant Account, Gateway, and related services are NOT FREE.  You will pay for the service.  

To get a merchant account relationship established, it is often best to talk with your bank to see what merchant account services they offer in conjunction with the business bank account you already hold with them.  Hopefully their services can utilize a gateway module already available within Zen Cart (see Admin > Modules > Payment).  

Alternatively, there is a list of [Payment-Provider Partners](https://www.zen-cart.com/content.php?14-Payment-Processing) which will give you competitive rates and also support the Zen Cart project at no additional cost to you.  

Be sure to research each provider's offerings to be sure they work with your banking details and meet your business requirements (volume, type of business, which bank, kinds of products sold, company reputation, etc etc etc).   

If you are new to merchant services, be sure to talk to a sales rep with a few providers and get educated on what the industry-standard fees, rate structures, services, and capabilities are, especially for your business niche.
The biggest confusion about payment collection for new storeowners is typically just a result of not understanding the payment-collection industry. When in doubt, ask questions.

## PayPal or other Online Banks

If you offer your customers the option to pay with a service that provides online funds services such as [PayPal](https://www.zen-cart.com/partners/paypal), then your customers will be directed to a page where they can login to that service, select their funding source (online funds or bank account or credit card, etc), and the complete their order.  Your money will be transferred from their online account to yours immediately. You can then arrange to have your money sent to your bank account. 
