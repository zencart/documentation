---
title: Adding a message to the admin order update email
description: Modifying emails which are sent when orders are updated 
category: email
weight: 10
---

Since Zen Cart 1.5.7, the capability to add a static message to the admin order update email has been built in.  The file containing the message is located at 'admin/includes/languages/english/email_extras.php'.  Edit this file, and set the defined constant `EMAIL_ORDER_UPDATE_MESSAGE` with your additional message and save the file.  

There is also a notifier called `ZEN_UPDATE_ORDERS_HISTORY_SET_ORDER_UPDATE_MESSAGE` which fires when the message is being added, providing the opportunity for customization.

You can test your changes to the order update email simply by updating an order on the [order details](/user/admin_pages/customers/orders/) page. 
