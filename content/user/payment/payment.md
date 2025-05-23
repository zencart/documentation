---
title: About Payment Modules 
description: What payment processing options are available? 
category: payment
weight: 1
---

Payment modules allow you to collect or arrange payment for an order.

The list of available payment modules may be seen by going to [Admin > Modules > Payment](/user/admin_pages/modules/payment/).

Zen Cart has a number of built-in payment modules: 

- [Authorize.net AIM](/user/payment/authorizenet_aim/)
- Check/Money Order - Receive payment by check
- Cash on Delivery - COD or in-person payment
- Free Order - required if you have free products in your store
- [PayPal](/user/payment/paypal/) using the older NVP/SOAP interface.

If you are just evaluating Zen Cart or running a test-only installation, 
then using the Check/Money Order module to process payments is the best option.

More payment modules may be found in the [Payment module section of the Plugins Library](https://www.zen-cart.com/downloads.php?do=cat&id=8).

The following integrations are highly recommended and well supported by their authors: 
- [Authorize.net CIM](https://www.zen-cart.com/downloads.php?do=file&id=2272)
- [Helcim](https://www.zen-cart.com/downloads.php?do=file&id=2402)
- [PayPal RESTful](/user/payment/paypal_restful/)
- [Square](/user/payment/square/)

Other options are: 
- [Braintree](https://www.zen-cart.com/downloads.php?do=file&id=1781)
- [NMI Gateway Processing Service-GPS Payment Module](https://www.zen-cart.com/downloads.php?do=file&id=2265)
- [Stripe](https://www.zen-cart.com/downloads.php?do=file&id=1548)

Some offline payment methods are also available: 
- [Invoice](https://www.zen-cart.com/downloads.php?do=file&id=131)
- [Quote](https://www.zen-cart.com/downloads.php?do=file&id=2199)

Developers wishing to create a payment module should see the [dev FAQs on modules](/dev/code/modules/). 

If you don't already have an account, please use these [direct links to the payment processors Zen Cart supports](https://www.zen-cart.com/content.php?14-Payment-Processing). By signing up via one of our links, you help support the Zen Cart project with small commissions that these providers give back to Zen Cart. Thank you in advance.

## Credit Card Payments 

Some credit card payment modules, such as Square, provide onsite payment.  The checkout payment page displays a form that captures the customer's credit card details.  

![Square Payment Form](/images/square_payment.jpg)


Other payment modules, like PayPal Express, collect payment offsite. They take the user to a form after checkout completion to collect payment, and pass the information back to Zen Cart.  The checkout payment page shows a radio button, which the customer clicks to select that method of payment.

![PayPal Express](/images/paypal_payment.png)

## Google Pay and Apple Pay

These payment methods are available in the most recent version of the [Square WebPay module](/user/payment/square/), which is available from [the Square WebPay developer](/user/payment/square_commercial_module/). 

## Manual Credit Card Processing 

In recent versions of Zen Cart, great care has been taken to handle payment details securely.  This means that older methods of capturing credit cards, such as the `cc` and `Ceon Manual Card` modules, are no longer recommended.  [Read more about why you shouldn't process credit cards manually](/user/payment/why_not_manual).
