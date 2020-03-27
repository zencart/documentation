---
title: Changing the Email Subject Line
description: Changing the Zen Cart Email Subject Line
category: email
weight: 10
---

Email subject lines typically consist of two parts, a piece of static text that says something like "Order Confirmation" or "Message from" and some dynamic content such as an order number or your store's name.

Changing the static text is straightforward. It is normally defined in the language file for the function that generates the email. Thus you would look in your `includes/languages/YOUR_LANGUAGE` folder (e.g. `includes/languages/english`) for the following files: `contact_us.php`, `create_account.php`, `checkout_process.php`, and `gv_send.php`. And within these files for a define statement for `'EMAIL_TEXT_SUBJECT'` or `'EMAIL_SUBJECT'`. 

You can then edit the associated text, but remember to save your changes to an override file (language overrides are described elsewhere in the docs). Remember also that if you  want to use an apostrophe or other special character, you must put a backslash in front of it (e.g. `define('EMAIL_TEXT_SUBJECT', 'Important Message from Simple Sammy\'s Smart Snail Store');` )

The "low stock email" is slightly different in that its `EMAIL_TEXT_SUBJECT` is defined in `email_extras.php`, but should still be overridden in the same way. 
The "order update" email is different again as it is generated from the admin side of your site and so the define statement is in `admin/includes/languages/YOUR_LANGUAGE/orders.php` which cannot be overridden. If you edit it, make sure you keep a copy (outside of your site) as backup.

Changing the dynamic data is more tricky and may require programming skills. But if you wanted, for example, to replace the "#" with "Number:" in the "order update email" you would search your site for where the subject's define constant is used (in this example, `EMAIL_TEXT_SUBJECT` is used twice in `admin/orders.php`) and replace the `' #'` that follows it with `' Number:'`.

