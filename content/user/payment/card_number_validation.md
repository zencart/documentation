---
title: Card Number Validation
description: How are credit cards validated? 
category: payment
weight: 10
---


#### How does Card Detection work? 

Zen Cart uses the standard Luhn Mod10 algorithm combined with the list of accepted cards you have configured in Admin > Configuration > Credit Cards. If the number fails validation or is a card-type that is not accepted based on your settings, it will be rejected with a "we do not accept that kind of card" error.

Wikipedia gives a good summary of [the anatomy of credit card numbers](https://en.wikipedia.org/wiki/Payment_card_number).  


### My customers get the error "Credit card not entered correctly" 
For some payment modules, Zen Cart evaluates the credit card number to see if they match the settings you have enabled in the Admin > Config > Credit Cards settings. This will reject disabled card-types before even sending to the merchant gateway.

So, if you enter a MasterCard number, but have MasterCard turned off (in the Admin), then it will tell the customer "we don't accept that kind of card".

Resolution:

1. Review your merchant account settings (ie: with your bank). Find out what credit card types you are allowed to process.

2. Then turn those on in Zen Cart under Admin > Configuration > Credit Cards

The error "We do not accept that kind of card" should  be handled the same way. 
