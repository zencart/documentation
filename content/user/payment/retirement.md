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

## Retirement Zen Cart versions prior to 2.0.0 

Since the Retired state is not available for older releases, you need to change some code to disable the display of the older PayPal modules.  Edit `includes/classes/payment.php`. In Zen Cart 1.5.8/1.5.8a, go to line 78.  Change 

```
              if ($class !='freecharger') {
```

to 

```
              if ($class !='freecharger' && $class != 'paypaldp' && $class != 'paypalwpp' && $class != 'paypal') {
```


