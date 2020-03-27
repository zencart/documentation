---
title: Collaboration
description: Zen Cart conference call on EU Digital VAT 
weight: 10
---

Precis of Conference Call 2014-12-30
=====================================

EU digital VAT Precis

 - Ian Wilson (wilt) Zen Cart Founder
 - Linda McGrath (ajeh) Zen Cart Founder
 - Enlightened 
 - Marge

I initially suggested there were two ways of supporting EU digital vat in Zen Cart
Either thru an integration with Taxamo, and with custom integration code for Zen Cart.
Those on the call were not really interested in a Taxamo integration based on the cost this would apply.

We then had some discussion of price display. So how do we apply differing vat percentages for EU countries, before a customer registers. The problem being that given we don't initially know a customer's location that prices may change as they move through the cart, and the fact that the prices may change, could cause cart abandonment. The only feasible solution here is some geoIP location.

Marge, who is from South Africa mentioned problems she would have, in terms of paying VAT to another country, due to SA currency rules. Hence, she wouldn't want to use the Taxamo option, but something that means she would not have to apply the Digital vat rules at all. The method Marge would prefer would be to have a manual email option which attached the downloadable product to the email.

Enlightened explained that this wouldn't work for her as the size of her downloadable products would probably run it to size limits for most email systems. She would need to use something like dropbox or similar to address that. However Enlightened said that even the email option would not suit her, as she runs a digital market place, where other craft suppliers sell through her website, and the size and volume of orders makes individual emails onerous.


Some discussion of the politics around exemption limits and the fact that in the future other countries may implement similar customer located tax rules.

Discussion then moved back to tax rates, and how we determine the rate for a particular product/customer location. Given the each EU country has 
a) A different base line tax rate
b) May have a different tax rate for digital goods/E-books etc
Enlightened suggested that she would like an automated system to update VAT rates, rather than have to manually change, especially when an EU country might change their rate for whatever reason.


Some discussion on enforcement. Given that VAT on E-Service Scheme (VoES) has been applicable since 2003, and as far as I know, no non EU supplier has been taken to court for non compliance, and also because HMRC have suggested they will take a very 'light touch' approach regarding compliance to the new rules for micro businesses, that even though the deadline was upon us, that businesses affected should not simply consider shutting down, but 'think' about how likely it would be that they would be detected. I of course also said, that I would never suggest a company should knowingly break the law :) 

Discussion returned to the fact that HMRC will now (at least till June 2015) accept the payment providers 'knowledge' of the customers location as definitive (rather than requiring 2 separate agreeing definitive tests of location). Again, we came back to the fact that while that would ease compliance, it didn't help with initial display of prices to 'guests'
Some clarification that the currency that prices are displayed would have no effect on other aspects of displaying prices with regard to EU Digital Vat

Enlightened highlighted this problem with showing prices, in that she would be deterred in buying (e.g. for Zen Cart Modules) if price changed between initial browsing, and checkout price.
(We haven't so far had any feedback from stores that sell Zen Cart Modules)

 Enlightened then asked about checking VAT numbers, in terms of separating B2B/B2C customers. I mentioned that there are already some contributions that allow for collection of VAT numbers, either at registration or at checkout. However, verifying those vat numbers is problematic. i.e. While api's exist to verify a VAT number exists, we can't verify that the person supplying that VAT number actually 'owns' the VAT number.
