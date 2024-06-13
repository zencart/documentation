---
title: Balance Owed Payments 
description: Taking payment for balances owed 
category: payment
weight: 10 
---

Sometimes the payment you received for an order is just not enough 

- the customer wanted to add items or options to the order
- shipping was more expensive than anticipated
- the customer requested additional services such as gift wrapping or insurance after completing their order

In cases like this, you must take another action to collect payment

### Option 1: Invoice the Customer 

Most credit card gateways and PayPal will allow you to send the customer a payable invoice.  Keep the order in Pending status until the invoice has been paid.

This image shows the [Square WebPay](/user/payment/square/) invoicing page:

![Square WebPay invoice](/images/square_invoice.png)


### Option 2: Take Payment through Your Cart Storefront

Create a $1 item in your store called "Pay outstanding balance" or something like that.  Set the item to Free Shipping, and be sure the [Free Shipping](/user/shipping/free_shipping/) shipping module is enabled.  Then [place an order](/user/running/login_as_customer/) for the customer with the balance, buying as many of the $1 item as are needed to satisfy the amount owed. (Once the item is in the cart and  the order is ready, you may need to ask the customer to login themselves and complete the order.)

### Option 3: Take Payment through Your Admin (Authorize.NET CIM)

If this is a very common situation for your business, you may consider using [Authorize.NET CIM](/user/payment/authorizenet_cim/) for payment processing.  CIM provides a mechanism for direct charges to a stored customer card if there is a balance owed (the "Get Money" button).  
 
