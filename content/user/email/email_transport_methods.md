---
title: Email Transport Methods 
description: SMTPAuth and other ways to send email 
category: email
weight: 10
---

## Email Transport methods explained
Zen Cart supports multiple email transport methods. 

Go to [Admin > Configuration > Email](/user/admin_pages/configuration/configuration_email/) and try them in this order:

1. "php" -- this uses whatever email method your webserver is configured to use for PHP mail commands, as set by your webhost.  This will work fine in most cases.
1. "smtp" or "smtpauth" -- for reliable email, many hosts require that you use "smtp" or usually "smtpauth" and set all the SMTP settings shown lower on the page.
1. "sendmail" -- if "php" doesn't work and you're not running a windows server, this is your next likely choice.
1. "sendmail -f" -- this is ideal in cases where your webserver configuration has some tighter security requirements -- esp in busy shared-hosting environments.

Zen Cart also supports the use of Qmail and Gmail. 

Using SMTPAuth, along with [DKIM and SPF](/user/email/advanced_email_troubleshooting/), is generally the most trouble-free way to send email from your cart. 

You may also wish to use SMTPAuth with [an external SMTP provider](/user/email/external_smtp_servers/) such as SMTP2Go or Mailgun. 

Using Google Mail can be problematic for a number of reasons: 

- If bad guys send spam through your contact us form, Google can decide you are a spammer and start blocking your email.  This could wind up making all your cart's emails (even order confirmations) non-deliverable. 

- Configuring Google Mail to work with an external system like Zen Cart requires you to reduce the security level of Google Mail. 

