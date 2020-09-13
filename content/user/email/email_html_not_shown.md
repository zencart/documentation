---
title: Why do emails not show in HTML format?
description: HTML email doesn't work 
category: email
weight: 10
---

HTML-formatted emails are SENT *only* when ALL of the following conditions are met:

*   HTML/MIME format is enabled in your admin
*   Customer has elected to choose HTML-formatted emails
*   You have the HTML email templates present in the /email/ folder of your site, and haven't changed permissions in any way that would prevent PHP from reading them (defaults are recommended)

Occasionally even though the email may be SENT in HTML format, it may ARRIVE without the HTML section displaying properly, for a few possible reasons:

1.  your hosting company's webserver stripped the HTML out because it appeared to violate a spam rule
2.  the recipient's hosting company stripped the HTML out because it appeared to violate a spam rule
3.  the recipient is using a free webmail-based email reader which alters the HTML content in a way that prevents your content from being displayed as desired
4.  you composed the email (altered the HTML in the template) to use advanced XHTML/CSS that's not supported by the recipient's email client
5.  the recipient is using an email program which doesn't render the HTML portion properly
6.  the recipient has changed their email program settings to disallow HTML content, either as a general rule or perhaps only from senders whom they've not whitelisted as known senders

Be sure to review the troubleshooting FAQs for other tips related to potential delivery problems.

- [Introduction to email](/user/email/email_introduction/)
- [Basic email troubleshooting](/user/email/emails_not_received/)
- [Advanced Email Troubleshooting](/user/email/advanced_email_troubleshooting/)  

