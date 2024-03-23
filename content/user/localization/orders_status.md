---
title: Order Statuses
description: Reflecting your order fulfillment process using order status
category: localization
weight: 10
---

### What is an Order Status? 

The order status field is a value which encapsulates where the order is in your workflow.
Zen Cart has the following default order statuses: 

- Pending
- Processing
- Delivered 
- Update 

New order statuses can be created in 
[Admin > Localization > Orders Status](/user/admin_pages/localization/orders_status/). 

### What is the initial status of an order?

When an order is first placed, by default it is put into status "Pending."  This can be overridden by most payment modules using the dropdown labelled "Set Order Status" in the payment module's own configuration.

"Pending" is a good status in the following situations: 
- For payment modules configured for [Authorize Only](/user/payment/auth_only/) rather than Authorize and Capture.
- For [offline payment modules](/user/payment/offline/), since you haven't received the money yet at the time the order is placed. 
- For any other unconfirmed or uncompleted payment. 

### How can I set my orders to status Shipped? 

You can add a new order status (Shipped) by going to
[Admin > Localization > Orders Status](/user/admin_pages/localization/orders_status/). 

Then go to [Admin > Customers > Orders](/user/admin_pages/customers/customers/) and update the order's status to 'Shipped' making sure that you set the *Notify Customer* radio button to *Email*.

