---
title: Fraud
description: Preventing fraudulent transactions 
category: security
weight: 10
---

Zen Cart has the following mechanisms for detecting and blocking fraudulent activity: 

- The [orders](/user/admin_pages/customers/orders/) screen has an indication at the left that the billing and shipping addresses are different.  This can in some cases be a clue that the order is fraudulent. 
- In Zen Cart 1.5.8 and above, the IP address used for account creation is tracked and displayed on the [Admin > Customers > Customers](/user/admin_pages/customers/customers/#customer-infobox) page in the right hand infobox when a customer is selected. 
- In Zen Cart 2.2.0 and above, the feature [Customer account activation](/user/orders/customer_approval/#customer-account-activation) may be used to ensure that customers are using valid email addresses they own for account creation.
- Payment modules each have their own [order status](/user/localization/orders_status/) for new orders.  Setting the status to "Pending" for a payment module allows you to check and ensure the payment went through before releasing the goods (virtual or physical).
- Plugins such as [Delete Spam Customers](https://www.zen-cart.com/downloads.php?do=file&id=2253) and [Activity Source](https://www.zen-cart.com/downloads.php?do=file&id=2418) allow you to track down and remove fraudulent entries from your database. 


