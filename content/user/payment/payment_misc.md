---
title: Payment Modules - Miscellaneous Questions
category: payment
weight: 5
---

{{< misc >}} 

---

## How do I authorize a Credit Card but not actually charge it until I ship the goods?

While many businesses will want to take payment immediately online, sometime the business model requires that the customer's card be authorized but **not charged** until the goods have been shipped.

Most gateways allow you to `authorize only` for the payment, and then within a week `capture` the payment when you ship the goods. 
The length of time allowed before `capture` depends on the contract you have with the Gateway (based on their rules, and on the kind of business you run).

To enable this, check whether your module has an option to specify `Authorize-Only` mode, and enable it. (As opposed to `Charge` or `Capture` mode.)

The process is this:
1. Customer places an order. The card is only `authorized`.
2. Prepare the order
3. Log in to your Merchant Gateway system. Find the transaction for that customer/order.
4. Choose the option to `Capture` the funds. This charges the card and puts the money in your bank account during the next settlement/processing batch.
5. Ship the goods

--- 

## My Payment Methods aren't showing up during checkout

During checkout, if your payment methods aren't showing up, go into Admin> Modules> Payment and check:

1. Is the payment module Installed? If not, click the Install button on the right-hand infobox.

2. Is it enabled? Some payment modules allow you to turn them on or off by clicking the Edit button and setting the status to true/false, on/off, etc. Some will auto-disable themselves if a fatal condition occurs (such as the gateway account credentials expired).

3. Do you have any Zone Restrictions associated with this payment module? If so, then likely by removing the Zone Restriction from the payment module will allow you to use it during checkout.
    You can use Zone Restrictions to limit which modules show up for different customer-billing-addresses (ie: different countries). To do this requires that you create zones to fully match the zones to your customers' addresses. If you are applying restrictions, always be sure to have at least one payment method WITHOUT any zones added to it, or else there will be customers who cannot go through checkout, and then you'll lose a sale!


---

## Card Number Validation

### Error: Credit card not entered correctly / We do not accept that kind of card

For some payment modules, Zen Cart evaluates the credit card number to see if they match the settings you have enabled in the Admin > Config > Credit Cards settings. This will reject disabled card-types before even sending to the merchant gateway.

So, if you enter a MasterCard number, but have MasterCard turned off (in the Admin), then it will tell the customer "we don't accept that kind of card".

Resolution:

1. Review your merchant account settings (ie: with your bank). Find out what credit card types you are allowed to process.

2. Then turn those on in Zen Cart under Admin > Configuration > Credit Cards

#### Card Detection

Zen Cart uses the standard Luhn Mod10 algorithm combined with the list of accepted cards you have configured in Admin > Configuration > Credit Cards. If the number fails validation or is a card-type that is not accepted based on your settings, it will be rejected with a "we do not accept that kind of card" error.

There are many online articles which go into more detail about the anatomy of credit card numbers.


---
<!-- please keep this at the end --> 
{{< faq_questions >}}
