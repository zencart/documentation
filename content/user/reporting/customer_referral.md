---
title: Customer Referral Processing
description: Rewarding customers who spread the word
category: reporting 
weight: 10
aliases:
    - /user/orders/customer_referral/
---

Zen Cart has referral-tracking functionality built-in, using coupon codes or using a customer-entered referral code. This can be ideal for tracking commissions for specific salespeople, crowdsourcing, campaign tracking, fundraising, etc.

### Configuring Tracking Using the Coupon Code

**a)** create a coupon

**b)**  give that coupon code it to your friend/salesperson/campaign/fundraiser/etc

**c)** they give it to their friend/mailinglist/fundraising-customer, who buys

**d)** the coupon code is stored as the referral source and tied to that customer when they place their order

Repeat steps **a**-**c** for the rest of your friends, and step **d** takes care of the rest.

Turn tracking on by going to [Admin > Configuration > Customer Details](/user/admin_pages/configuration/configuration_customerdetails/) and setting  *Customers Referral Status* = 1:


### Configuring Tracking Using Customer Entered Values 

Turn tracking on by going to [Admin > Configuration > Customer Details](/user/admin_pages/configuration/configuration_customerdetails/) and setting  *Customers Referral Status* = 2:


### Tracking the Results
In the Admin > Reports menu there is a [Customers Referral](/user/admin_pages/reports/customers_referral/) report, which shows you the sales made to customers using those coupons or tracking codes.

### Related Topics:
Affiliate tracking would probably be handled differently by engaging a third-party software tool, using a method similar to what is described in the following articles:

[Adding a tracking pixel](/user/template/tracking_pixel/)

[Integrating Sales Analytics/Affiliate Tools](/user/orders/sales_analytics_affiliate_tools/)

