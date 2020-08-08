---
title: Payment Modules - Miscellaneous Questions
category: payment
weight: 5
---

{{< misc >}} 

---
### Credit card not entered correctly / We do not accept that kind of card

Zen Cart evaluates the credit card numbers you enter to see if they match the settings you have enabled in the Admin > Config > Credit Cards settings.

So, if you enter a MasterCard number, but have MasterCard turned off (in the Admin), then it will tell the customer "we don't accept that kind of card".

It doesn't matter which credit card gateway you have installed.  The same processing will reject disabled card-types before even sending to the merchant gateway.

Resolution:

1. Review your merchant account settings (ie: with your bank). Find out what credit card types you are allowed to process.

2. Then turn those on in Zen Cart under Admin > Configuration > Credit Cards

3. Then enable your payment module in Zen Cart.

---

#### MORE INFORMATION YOU MIGHT FIND USEFUL
Zen Cart uses the MOD10 approach (google it) combined with the list of accepted cards you have configured in Admin > Configuration > Credit Cards. If the number fails validation or is a card-type that is not accepted based on your settings, it will be rejected with the error message you mentioned.

You might also note that Zen Cart uses these Credit Card Prefix Patterns (and more) to detect which kind of card your customer has entered.

* Visa: 13 or 16 numbers starting with 4

* MasterCard: 16 numbers starting with 5

* Discover: 16 numbers starting with 6011

* AMEX: 15 numbers starting with 34 or 37

There are many other articles, especially on Wikipedia, about the anatomy of credit card numbers.

--- 
### My Payment Methods aren't showing up during checkout

During checkout, if your payment methods aren't showing up, go into Admin> Modules> Payment and check:

1. Is the payment module Installed? If not, click the Install button on the right-hand infobox.

2. Is it enabled? Some payment modules allow you to turn them on or off by clicking the Edit button and setting the status to true/false, on/off, etc.

3. Do you have any Zones associated with this payment module? If so, then likely by removing the Zone configuration from the payment module will allow you to use it during checkout.

To properly configure zones with payment modules requires that you create zones to fully match the zones to your customers' addresses. Always be sure to have at least one payment method WITHOUT any zones added to it, or else there will be customers who cannot go through checkout, and then you'll lose a sale!


---
### How do I authorize a Credit Card but not actually charge it until I ship the goods?

**Question:**

After taking the order in Zen Cart I want the Credit Card to be authorised but not charged to the customer until the goods have been shipped.  I would anticipate the delay from order to shipping to be about a week. How do I go about this?

**Answer:**

This largely depends on your choice of payment gateway, as to whether this option is offered or not.  Most true Merchant Gateways offer this, including Authorize.net AIM.

It is very common to need to prepare the order, then calculate true shipping costs, and update those costs before finally charging the card.  Or at least not charge until the goods are ready to ship.

The process is this:
1. Set the payment module into "Authorize Payment" mode (not "Capture" or "Charge" mode).
2. Prepare the order
3. Calculate true shipping charges.
4. Log in to your Merchant Gateway system. Find the transaction for that customer/order.  Update shipping costs if appropriate.  Now choose to "Capture" the funds.  This charges the card and puts the money in your bank account during the next processing cycle.
5. Ship the goods


---
<!-- please keep this at the end --> 
{{< faq_questions >}}
