---
title: Customizing Email
description: Changing the appearance of email sent by Zen Cart 
category: email
weight: 10
---

There are several places in the Zen Cart code where e-mails to the customer are constructed. To create a consistent feel for all your communication with the customer, you will want to make sure you modify all these places whenever you modify one. 

Don't forget to use the [template overrides system](/user/template/template_overrides/) wherever possible when making your changes and if this is not available look for notifiers and use the [observer/notifier system](/dev/code/notifiers/) to make your changes.

The e-mail's structure is determined in one of two ways: if you are sending plain text e-mails, it is determined by the way you put together the various items (customer greeting, order number, link to detailed invoice, etc) in a string variable that is then passed to the `zen_mail()` function. If you are sending HTML e-mails, the structure is determined by the template you use.

## Plain text e-mails

You can rearrange, add, or delete items in a plain text e-mail. To do so, you will need to either, use the [template overrides system](/user/template/template_overrides/),  the [observer/notifier system](/dev/code/notifiers/) or as  a last resort edit the Zen Cart files where the e-mail is created. For example, if you want to edit the order confirmation e-mail, you will need to edit the file `includes/classes/order.php`.

In our example, we open up `includes/classes/order.php` and scroll down to the bottom of the file, in the function `send_order_email()`. There you will see the lines that construct the plain text e-mail message:

```
(line 1302)        $email_order = EMAIL_TEXT_HEADER . EMAIL_TEXT_FROM . STORE_NAME . "\n\n" .
                       $this->customer['firstname'] . ' ' . $this->customer['lastname'] . "\n\n" .
                       EMAIL_THANKS_FOR_SHOPPING . "\n" . EMAIL_DETAILS_FOLLOW . "\n" .
                       EMAIL_SEPARATOR . "\n" .
                       EMAIL_TEXT_ORDER_NUMBER . ' ' . $zf_insert_id . "\n" .
                       ... 
```

```
(line 1327)          $email_order .= zen_output_string_protected($this->info['comments']) . "\n\n";
```

```
(line 1334)        $email_order .= EMAIL_TEXT_PRODUCTS . "\n" .
                        EMAIL_SEPARATOR . "\n" .
                        $this->products_ordered .
                        EMAIL_SEPARATOR . "\n";
```

and so on. In this file, the variable that holds the plain text e-mail message is called `$email_order`; it generally has a different name in each file, such as `$email` or `$email_text`. Whatever its name, this is the place where you can make your changes, if you cannot use [overrides](/user/template/template_overrides/) or  [notifiers](/dev/code/notifiers/). You can add, delete, and rearrange the order of the items to suit your wishes.

Remember if you change core files you will have to do it for every upgrade.

If you don't understand what's going on in the lines above, you may want to [Read more about PHP first](http://php.net).

## HTML e-mails

The HTML e-mail templates are located in the folder `email/` in your store's root directory. There are several different templates, each for a different purpose. You can rearrange the items, add new items, or delete items to achieve the structure you want for your e-mails.

You need not edit any other Zen Cart files if you just want to rearrange or delete the items listed in an HTML template. To add items, however, you will need to find all the Zen Cart files that use that particular HTML template, and add in a definition for your new item. You can use the [Developer's Tool Kit](/user/admin/developers_toolkit/).
in the Admin to find all the files that use a given template; search for the last part of the template name. For example, if you want to add an item into the HTML template `email_template_order_status.html`, search for `order_status` using the [Developer's Tool Kit](/user/admin/developers_toolkit/).

Once you have found the files that need to be edited, you will want to add a definition for your new HTML item to each one. For example, suppose you have added an item called `$EMAIL_HOURS_OF_OPERATION` to the `email_template_order_status.html` template. One of the files that you will need to edit is `admin/orders.php`. Find the part of that file where the e-mail message is being constructed; in this case, it begins around line 100\.

You see that the HTML message is constructed with several statements like this:

```
      $html_msg['EMAIL_CUSTOMERS_NAME'] = $check_status->fields['customers_name'];
      $html_msg['EMAIL_TEXT_ORDER_NUMBER'] = EMAIL_TEXT_ORDER_NUMBER . ' ' . $oID;

```
All you need to do is add a new statement under all these to define your new item:

```
      $html_msg['EMAIL_HOURS_OF_OPERATION'] = 'We are open from 9 AM to 5 PM every day of the week.';
```

Of course, it's a better idea to use a constant instead of hardcoding your text like this, but we'll do it like this in our example for clarity's sake.

Use a $ in front of the name of your new item in the HTML template, but do not use the $ where you define it.

## Finding files where e-mails are created

Here is a list to help you find the files you will need to edit to modify the structure of your e-mails.

<table border="1" cellpadding="2">

<tbody>

<tr>

<th width="150">Type of e-mail</th>

<th width="225">HTML template in folder email/</th>

<th width="125">Search for this in Developer's Tool Kit</th>

</tr>

<tr>

<td>Contact Us</td>

<td>email_template_contact_us.html</td>

<td>'contact_us'</td>

</tr>

<tr>

<td>Coupon</td>

<td>email_template_coupon.html</td>

<td>'coupon'</td>

</tr>

<tr>

<td>Default</td>

<td>email_template_default.html</td>

<td>'default'</td>

</tr>

<tr>

<td>Direct e-mail</td>

<td>email_template_direct_email.html</td>

<td>'direct_email'</td>

</tr>

<tr>

<td>Gift Certificates</td>

<td>email_template_gv_mail.html  
email_template_gv_send.html  
email_template_gv_queue.html</td>

<td>'gv_mail'  
'gv_send'  
'gv_queue'</td>

</tr>

<tr>

<td>Low stock</td>

<td>email_template_low_stock.html</td>

<td>'low_stock'</td>

</tr>

<tr>

<td>Newsletters</td>

<td>email_template_newsletters.html</td>

<td>'newsletters'</td>

</tr>

<tr>

<td>Order confirmation</td>

<td>email_template_checkout.html</td>

<td>'checkout'</td>

</tr>

<tr>

<td>Order Status update</td>

<td>email_template_order_status.html</td>

<td>'order_status'</td>

</tr>

<tr>

<td>Password forgotten</td>

<td>email_template_password_forgotten.html</td>

<td>'password_forgotten'</td>

</tr>

<tr>

<td>Product notification</td>

<td>email_template_product_notification.html</td>

<td>'product_notification'</td>

</tr>

<tr>

<td>Welcome</td>

<td>email_template_welcome.html</td>

<td>'welcome'</td>

</tr>

</tbody>

</table>

## Modifying the Order Confirmation email 
A commonly requested change is adding a message to the email your 
customers get when they place an order. 
This is documented in [How can I add a message to my order confirmation emails? 
](/user/email/add_message/).

