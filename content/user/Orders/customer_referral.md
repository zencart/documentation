---
title: Customer Referral Processing
category: orders 
weight: 10
---

Zen Cart has referral-tracking functionality built-in, using coupon codes. This can be ideal for tracking commissions for specific salespeople, crowdsourcing, campaign tracking, fundraising, etc.

a) create a coupon

b) give that coupon code it to your friend/salesperson/campaign/fundraiser/etc

c) they give it to their friend/mailinglist/fundraising-customer, who buys

d) the coupon code is stored as the referral source and tied to that customer when they place their order

Repeat steps a-c for the rest of your friends, and step d takes care of the rest.

Turn the whole thing on via Admin->Configuration->Customer Details->Customers Referral Status = 1:

Customers Referral Status

Customers Referral Code is created from

0= Off

1= 1st Discount Coupon Code used

2= Customer can add during create account or edit if blank

**NOTE:** Once the Customers Referral Code has been set it can only be changed in the Admin->Customers screen.

Tracking the Results
In the Admin->Reports menu there is a Customers Referral Tracking report which shows you the sales made to customers using those coupons.


### Related Topics:
Affiliate tracking would probably be handled differently by engaging a third-party software tool, using a method similar to what is described in the following articles:

[Adding a tracking pixel](/user/template/tracking_pixel/)

[Integrating Sales Analytics/Affiliate Tools](/user/orders/sales_analytics_affiliate_tools/)

