---
title: Resend Order Confirmation Email
description: I need to resend the checkout email to a customer
category: Running
weight: 10
---

Sometimes customers need you to send an invoice or a copy of their checkout confirmation email. 

This can happen for a variety of reasons:

- the customer created an account but [mis-typed their email](/user/running/mistyped_email/). 
- they need an invoice for tax or record keeping purposes. 
- your cart has an [email deliverability issue](/user/email/emails_not_received/) so they never received their original order confirmation. 

Here are a few ways you can get them the information they need. 

## Forward them the Admin order confirmation 
The administrator gets a confirmation email for each order, as long as the _Send Copy of Order Confirmation Emails To_ field in [Email Settings](/user/admin_pages/configuration/configuration_email/) is set. 

Note that the administrator copy of the confirmation email has additional content at the bottom, which you may want to trim prior to forwarding. 


## Creating a PDF Invoice from Admin 
1. Go to Admin > Customers > Orders click on the order
1. In the sidebar on the right, there is a button for Invoice
1. Click the invoice button
1. On the new page that opens, do a Print (either using Control-P or your browser's Print button from the File menu)
1. A dialog will come up, and prompt you to select a printer.  Select "Save as PDF".
1. Email the customer the resultant PDF of their order. 

![Save as PDF](/images/save_as_pdf.png)

## Encouraging self service 
Tell the customer to login to their account and click the "My Account" link, where they can see all their past orders, and click through to the specific one.
They can print that screen, either to paper or PDF (see above).

If your store needs to let customers make a PDF on a regular basis, the [Catalog Invoice](https://www.zen-cart.com/downloads.php?do=file&id=2111) plugin might be of interest.

## Using the Email Archive Manager 

If you had [email archiving](/user/admin_pages/configuration/configuration_email#email_archiving_active) turned on at the time the order was placed, you can use the [Email Archive Manager](/user/email/email_archive_manager/) to resend the email. 

