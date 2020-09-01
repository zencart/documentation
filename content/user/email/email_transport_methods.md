---
title: Emails Transport Methods 
description: PHP, SMTP, SMTPAuth and Sendmail 
category: email
weight: 10
---

## Email Transport methods explained
Zen Cart supports multiple email transport methods. 

Go to [Admin > Configuration > Email Options](/user/admin_pages/configuration/configuration_emailoptions/) and try them in this order:

1. "php" -- this uses whatever email method your webserver is configured to use for PHP mail commands, as set by your webhost.  This will work fine in most cases.
1. "smtp" or "smtpauth" -- for reliable email, many hosts require that you use "smtp" or usually "smtpauth" and set all the SMTP settings shown lower on the page.
1. "sendmail" -- if "php" doesn't work and you're not running a windows server, this is your next likely choice.
1. "sendmail -f" -- this is ideal in cases where your webserver configuration has some tighter security requirements -- esp in busy shared-hosting environments.
1. "qmail" --  for linux/unix hosts running `Qmail` as `sendmail` wrapper at `/var/qmail/bin/sendmail`.

