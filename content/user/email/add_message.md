---
title: Adding a message to the checkout email
description: How do I add a message to my order confirmation emails? 
category: email
weight: 10
---

In Zen Cart 1.5.6, a plugin called [Order Message](https://www.zen-cart.com/downloads.php?do=file&id=2200) was pulled into the Zen Cart core.  To use it, 
edit the file 
`includes/languages/english/YOURTEMPLATE/email_extras.php`
and set the defined constant 
`EMAIL_ORDER_MESSAGE` with your message.  

If your Zen Cart version is prior to 1.5.6, you may still use the Order Message plugin. 

