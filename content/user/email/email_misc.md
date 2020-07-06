---
title: Miscellaneous Email Questions
description: About email in Zen Cart 
category: email 
weight: -1 
---

{{< misc >}}

---
### How can I add a message to my order confirmation emails? 

In Zen Cart 1.5.6, a plugin called [Order Message](https://www.zen-cart.com/downloads.php?do=file&id=2200) was pulled into the Zen Cart core.  To use it, 
edit the file 
`includes/languages/english/YOURTEMPLATE/email_extras.php`
and set the defined constant 
`EMAIL_ORDER_MESSAGE` with your message.  

If your Zen Cart version is prior to 1.5.6, you may still use the Order Message plugin. 

--- 
### How can I email all my customers about a sale or promotion? 

Sending large numbers of emails from your own hosting account 
is no longer recommended.  
See [Newsletters](/user/email/newsletters) for alternatives. 

---
### Where are the emails sent by Zen Cart stored? 

By default, sent emails are not stored.  You may however turn on saving emails
using setting the [Email Archiving Active](/user/admin_pages/configuration/configuration_emailoptions/#email_archiving_active) configuration value to *true*, and you may view stored emails using [Email Archive Manager](/user/email/email_archive_manager/). 

**NOTE:** This `email_archive` table, where emails are stored, grows large
quickly, so be sure to cull it frequently. 

---
<!-- please keep this at the end --> 
{{< faq_questions >}}

