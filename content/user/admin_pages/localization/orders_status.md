---
title: Orders Status 
category: admin_pages
weight: 30
---

The [Order Status](/user/localization/orders_status/) field encapsulates where 
the order is in your order processing workflow. 

It can be set on the [order details](/user/admin_pages/customers/orders/) page in the box that allows you to add entries to the order history.

The Admin > Localization > Order Status  page allows you to add names of new order status entries, edit existing order status name entries, or delete an order status name entry.

## Add a new Order Status
To add a new order status, click on the insert button. A box allowing you to enter the name of the status will appear. If this is the default status, check the set as default box. Click on the insert button to save this new status, click on the cancel button to discard.


## Edit an existing Order Status
Click on the name of the status you want to change, so that the right arrow appears in the action column, then click on the edit button. Type in the new name for this status. If this is the default status, check the set as default box. Click on the update button to save this change of order status, click on the cancel button to discard the change.


## Delete an Order Status
Click on the name of the status you want to remove, so that the right arrow appears in the action column, then click on the delete button. You will be asked to confirm this action. Click on the delete button again to remove this order status, click on the cancel button if you do not wish to remove it. If this is the default order status you will not be able to delete it.

## Color Coding

In Zen Cart 2.2 and above, order statuses may be color coded.  

![Order status color coding](/images/order_status_color_coding.png)

The status column on the orders page will then show the order status in its color code.  See [Admin > Orders](/user/admin_pages/customers/orders#colors).

Some suggested color codes for the default order statuses would be: 

- Pending = #f0ad4e
- Processing = #5bc0de
- Delivered = #5cb85c
- Update = #ff00ff

which would yield labels that look like this: 

<span style="color: white; padding: .2em .6em .3em; border-radius:0.25em; border-color: #f0ad4e; background-color: #f0ad4e;">**Pending**</span>

<span style="color: white; padding: .2em .6em .3em; border-radius:0.25em; border-color: #5bc0de; background-color: #5bc0de;"> **Processing**</span>

<span style="color: white; padding: .2em .6em .3em; border-radius:0.25em; border-color: #5cb85c; background-color: #5cb85c;">**Delivered**</span>

<span style="color: white; padding: .2em .6em .3em; border-radius:0.25em; border-color: #ff00ff; background-color: #ff00ff;">**Update**</span>

