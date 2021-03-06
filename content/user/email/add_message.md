---
title: Adding a message to the checkout email
description: How do I add a message to my order confirmation emails? 
category: email
weight: 10
---

Since Zen Cart 1.5.6, the capability to add a static message to every email has been built in.  The original file is located at 'includes/languages/english/email_extras.php'. If you edit the file, save it as `includes/languages/english/YOURTEMPLATE/email_extras.php` to add it to your template's override.  If the file already exists at 'includes/languages/english/YOURTEMPLATE/email_extras.php', then set the defined constant `EMAIL_ORDER_MESSAGE` with your additional message and save the file.  

If your Zen Cart version is older than 1.5.6, you may use the [Order Message](https://www.zen-cart.com/downloads.php?do=file&id=2200) plugin.
