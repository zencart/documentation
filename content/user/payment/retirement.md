---
title: Retirement for a Payment Module 
description: Disabling storefront access to a payment module while keeping its admin capabilities 
category: payment 
weight: 10
---

Since 2.0.0, select payment modules may be put in a state between Enabled and Disabled called "Retired."

![Retired Status](/images/retired.png)

Setting a payment module to "Retired" disables it so that new orders may not be placed with it, but still allows admins to process existing older orders which used that payment method. 

Retirement is currently available for PayPal Express and PayPal Website Payments Pro to enable a smooth transition to [PayPal RESTful](/user/payment/paypal_restful/).

