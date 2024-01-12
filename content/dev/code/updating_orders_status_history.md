---
title: Adding a Status History Record to an Order
description: How to use the zen_update_orders_history function 
category: code
weight: 10
---

Zen Cart version 1.5.6 introduced the function `zen_update_orders_history`, providing a way for both admin and storefront processing to easily update an order's status-history, e.g. changing an order's status from `Processing` to `Delivered`.  That function also, based on the parameters supplied, sends an optional status-update email to the customer, interested admins or both.

The function was initially created for a site-specific change where the processing was 'interested' in an order's ***change*** in status.  See [Notifications Issued](#notifications-issued)  for additional information.

## Function Interface

The function `zen_update_orders_history` provides an easy way to update an order's status-history, with the option of sending an email message to the ordering customer.  It takes a bunch of parameters, described below.

```php
int zen_update_orders_history($orders_id, $message = '', $updated_by = null, $orders_new_status = -1, $notify_customer = -1, $email_include_message = true, $email_subject = '', $send_extra_emails_to = '')
```

1. `$orders_id`.  Contains the (integer) orders_id of the to-be-updated customer order.
2. `$message`.  Contains a message-string to be recorded with the status-update.
3. `$updated_by`.  If the value *is not* `null`, then it's expected to be a string-value that identifies 'who' (e.g. an  external process) caused the update.  Otherwise, the `$updated_by` value is set based on 
   1. ... if in the admin, to the current admin-name suffixed by their admin ID, e.g. `Dave [5]`.
   2. ... if a customer is logged in, to an empty string.
   3. ... if a customer is not logged in, to `N/A`.
4. `$orders_new_status`.  Indicates the new status-history value to be applied to an order.  A value of **-1** indicates no change in status.
5. `$notify_customer`. Indicates whether the added status-history record is customer-visible and whether to send an email notification of the change, one of:
   - 0 ... No emails are sent; the history-update is visible to the customer.
   - 1 ... Emails are sent to the customer and any configured admins; the history-update is visible to the customer.
   - -1 ... No emails are sent; the history-update is **not** visible to the customer.
   - -2 ... Emails are sent to any configured admins; the history-update is **not** visible to the customer.
6. `$email_include_message`.  A boolean flag that indicates whether or not to include the `$message` string as part of the to-be-sent email.  If `false`, the message will be recorded in the status-history update only.
7. `$email_subject`.  A `string` value, providing an override to the default subject: `OSH_EMAIL_TEXT_SUBJECT . ' #' . $orders_id`.
8. `$send_extra_emails_to`. A `string` value, providing an override for the database constant `SEND_EXTRA_ORDERS_STATUS_ADMIN_EMAILS_TO`.

The function returns an integer value, identifying its completion status, one of:

- -1 ... No status-change detected, no `orders_status_history` record was written.
- -2 ... No order-record was found for the submitted `$orders_id`. 
- Otherwise, the return value identifies the `orders_status_history_id` value for the just-written status-history record.

## Function Processing

### Creating an Order's Status History Record

The `zen_update_orders_history` function will create an additional `orders_status_history` record for the supplied `$orders_id` if the `$orders_id` supplied is associated with an `orders` table record and at least one of the following conditions is met:

1. The `$orders_new_status` is set to -1 (no change in status).
2. The `$orders_new_status` is different from the order's current status.
3. The `$message` to be recorded is not 'empty'.

### Typical Function Call for Plugin Authors/Developers

You have just taken an action that you want recorded in the order status history table.  Simply pass in the order id and a string with what you want recorded.

```
zen_update_orders_history($oID, 'A comment describing the action taken');
```

No email is sent and the entry is only shown in the admin. 

### Notifications Issued

The function also provides a collection of notifications, enabling additional store-specific processing.

#### ZEN_UPDATE_ORDERS_HISTORY_PRE_EMAIL

This notification is issued only when `$email_include_message` is set to true (i.e. the message is to be included in any sent emails) and provides a watching observer the opportunity to override the current message text:

```php
$GLOBALS['zco_notifier']->notify('ZEN_UPDATE_ORDERS_HISTORY_PRE_EMAIL', array('message' => $message), $osh_additional_comments);
```

The `$osh_additional_comments` parameter can be updated to provide additional text to be appended to the `$message` value for the emails.

#### ZEN_UPDATE_ORDERS_HISTORY_STATUS_VALUES

This notification is issued if the function has determined that an orders-status-history record is to be created:

```php
$GLOBALS['zco_notifier']->notify('ZEN_UPDATE_ORDERS_HISTORY_STATUS_VALUES', array('orders_id' => $orders_id, 'new' => $orders_new_status, 'old' => $orders_current_status));
```

The notification identifies the orders-id as well as the order's new (to-be-written) and current orders' status values and is the _heart_ of the function's processing.  Essentially the notification provides a means for site-specific changes to be performed when an order's status ***changes***.

#### ZEN_UPDATE_ORDERS_HISTORY_SET_ORDER_UPDATE_MESSAGE

This notification is issued prior to sending any email and gives a watching observer the opportunity to override the text sent in that email.

```php
$GLOBALS['zco_notifier']->notify('ZEN_UPDATE_ORDERS_HISTORY_SET_ORDER_UPDATE_MESSAGE', $orders_id, $email_order_message);
```

#### ZEN_UPDATE_ORDERS_HISTORY_BEFORE_INSERT

This notification is issued just prior to creating a new `orders_status_history` record for the order, giving a watching observer the opportunity to make final adjustments, e.g. adding additional fields to the status-history record:

```php
$GLOBALS['zco_notifier']->notify('ZEN_UPDATE_ORDERS_HISTORY_BEFORE_INSERT', array(), $osh_sql);
```

The `$osh_sql` is an associative array, submitted to `zen_db_perform` to create that new record.
