---
title: Email Archive Manager 
description: Keeping a record of email sent by Zen Cart 
category: email
weight: 10
---

The [Email Archive Manager plugin](https://www.zen-cart.com/downloads.php?do=file&id=101) allows you to view the emails sent by the cart within your Admin panel.  This can be useful in a number of situations: 

- You are modifying the HTML email templates or email construction logic and you want to quickly see both the text and HTMl emails 
- You need a log of the email your customer service staff are sending
- You want the historical record of emails that went out

The main screen for Email Archive Manager is a listing of all recorded emails sent by the cart.  

![Email Archive Listing](/images/email_archive_listing.png)

Clicking on any particular line provides a brief view of the email, and an opportunity to open the entire email in TEXT or HTML format (if so configured). 

![Email Archive Detail](/images/email_archive_detail.png)

To use the Email Archive Manager, you must enable email archiving in 
[Admin > Configuration > Email](/user/admin_pages/configuration/configuration_email#email_archiving_active).

Note that email archiving does consume a significant amount of database space, and periodic trimming of the archive is recommended.  The Email Achive Manager has a built-in trim function that allows you to delete email older than 1 month, 6 months or 12 months from within your Zen Cart admin. 
