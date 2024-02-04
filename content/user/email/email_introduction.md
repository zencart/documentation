---
title: Introduction to Email in Zen Cart 
description: Overview of the email system 
category: email
weight: 1
---

Zen Cart's email infrastructure is largely dependent on the services available to your webserver. This includes internet connection issues, available ports, as well as PHP configuration options and the programs/services running on your server.

## Zen Cart Email Infrastructure Explained

Here's how Zen Cart's email interface works:

1.  _Admin_ and _Store_ both use the same infrastructure.
2.  Zen Cart uses PHPMailer for sending mail.
3.  Wherever an email is sent, it is initiated via `zen_mail()` which is in the `includes/functions/functions_email.php`. This builds the email object according to all your settings in Admin > Config > Email.
    *   transport method: PHP, smtp, sendmail, sendmail-f, smtpauth, etc.
    *   text-only vs HTML formatted
    *   sent to, sendfrom
    *   ... everything from that section, really.
4.  Then it hands the email off to PHPMailer to send it.
    *   If the transport is SMTP/SMPTAUTH, then direct communication with the specified mailserver is initiated. **SMTPAUTH IS THE RECOMMENDED TRANSPORT.**
    *   If the transport is "PHP", then the server's PHP configuration takes over entirely, using whatever PHP has been configured to use in the server's php.ini settings.
    *   If the transport is a sendmail function, then the server attempts to use the sendmail program on your webserver.
5.  If email archiving is enabled and no error message is encountered (ie: the email is delivered without being rejected by the sending server), the email is stored to the `email_archive` database table. Note that if you wish to use email archiving, you probably also want to use the [Email Archive Manager](/user/email/email_archive_manager/). 
6.  If an error occurs, then the error details are logged into the /logs/ folder as "myDEBUG-xxxxxx.log" files.  See [reading a myDEBUG log](/user/troubleshooting/debug_logs/). 

## Prerequisites

1.  Your webserver must have a mail service enabled. For Linux/Unix hosts, this is typically done via sendmail or exim or qmail daemons. On Windows servers, this may be done via services offered with IIS.
2.  Your webserver must allow email connections from PHP.
3.  If you are using sendmail options, then the PHP configuration for sendmail functions must be configured properly on the server.
4.  You must have an unrestricted connection to the mailserver you're sending through.
    *   If you are running from a home-based server (ie: for testing), note that your ISP may automatically have port 25 blocked so that you have to send mail through their server. In this case, use SMTP for your transport method, and supply your ISP's mailserver as your SMTP host.
    *   If your webhost mailserver is reachable on another port, supply that port number in the SMTP settings.

## Diagnosing Problems

1.  change transport methods (ask your host what's best ... they should know how they've configured your server).
    *   **NOTE:** `SMTPAUTH` is least likely to end up getting treated as spam.
2.  change send-from email addresses (Admin > Configuration > Email). This should be an email associated with your server's domain. Preferably not a "free email account" such as Gmail, since your server is *not* a Gmail server and therefore your emails would be seen as spammy impersonation attempts, unless you're using SMTPAUTH properly configured for your account.
    *   MAKE SURE THE ADDRESS IS VALID.
    *   It is recommended to use an email account linked to the same domain name as your store. Attempting to masquerade with a different email address makes your emails prime candidates for being treated as junkmail, and thus not delivered.
3.  change send-to email addresses ... DO NOT TEST USING FREE MAIL SERVICES ... your mail is often dropped to a junkmail black hole.
4.  be sure there are no embedded carriage returns in your send-to email addresses.
5.  check your junkmail settings.
6.  research whether your mailserver or hosting company is blacklisted (you can check [http://www.mxtoolbox.com/blacklists.aspx](http://www.mxtoolbox.com/blacklists.aspx) or search online for _smtp blacklist_ for additional resources)
7.  try setting the option for **Emails must send from known domain?** to true. This causes the email "sender" address to be more aligned to your own website, and thus less likely to be rejected while processing. This should always be set to true nowadays.
8.  try testing with HTML emails OFF, since many spam filters block HTML-formatted messages before they even get out the gate.
9.  check the mailserver logs ... is it complaining about something, either inbound or outbound?
10.  for kicks, get the webserver/mailserver rebooted and dump all the logs ... just maybe something's runamuck in there ...
11.  Try enabling Email Archiving (Admin > Configuration > Email > Email Archiving). Then install the [Email Archive Manager](/user/email/email_archive_manager/) from the Zen Cart Downloads section (in admin tools), and confirm that the emails are actually being sent from Zen Cart. If it's in the archive, it was handed off to the mailserver. Once the email leaves Zen Cart, it's at the mercy of your mailserver.
12.  Look at your raw/full email headers. Does the "from" address appear to be a "nobody@xxxxxxx" address? Some hosts block these. The "email must send from known domain" setting is designed to counteract this. The SMTPAUTH setting also helps to work around this.
13.  This is RARE: If using "sendmail" and your "sendmail" path on your webserver is not the default of /usr/sbin/sendmail then you can override the default by adding a definition for it in a new file on your server: /includes/extra_datafiles/email_sendmail_override.php ... create a define for EMAIL_SENDMAIL_PATH and point it to the actual sendmail path for your particular host. This should not be necessary, and usually using "PHP" as transport method will correct it without making this edit.
14.  Also rare: Does your server require 7bit mail encoding instead of the default 8bit? If so, edit the /includes/extra_configures.email_use_8bit.php file and put // before the define statement there.

If the email doesn't get to its destination, then usually the problem is a misconfiguration of the MTA or the host is blacklisted somewhere, or ports are blocked or ... well ... the probable causes are for a system administrator to understand.

### More Troubleshooting Ideas 

- [Basic email troubleshooting](/user/email/emails_not_received/)
- [Advanced Email Troubleshooting](/user/email/advanced_email_troubleshooting/)  

### Troubleshooting Questions for your Hosting Company

Have you asked your hosting company what the right configuration is for your server to send mail most appropriately?

As far as Zen Cart is concerned, you have these options. Ask your host what they require:

1.  Mail Transport ... best to use SMTPAUTH, and supply your mailbox credentials in the SMTP settings
2.  Emails must send from known domain ... true/false (ie: does the server accept emails that have "from headers" set to external domains, or only it's own domains?) Best to set to true.
3.  SMTP port to use ... 25, or 587 for TLS, or sometimes 465 for old SSL mode.

If your "contact us" emails are not arriving at the desired destinations, try emptying the "contact us pulldown" list. This will force it to use your Store Owner email address and bypass the occasional confusion encountered with properly formatting addresses for the pulldown list.

As mentioned earlier, if the emails are showing in the archive log (assuming you've enabled it), then Zen Cart is generating the message and handing it off to your webserver to send. If it's not being delivered, then either your webserver is dumping it, or the recipient is not getting it, possibly due to frequent spam from your webhost or other reasons. **Perhaps your hosting company will offer you some assistance or at least explain how their servers are configured so that you can determine the right setting for your hosting environment. They know your server better than anyone.**

Ask your host whether your/their mailserver is blacklisted by anyone. If so, try to get the blacklisting removed.

Is your account's SPF record correct? DKIM?  In cPanel you can add SPF and DKIM records using the "Email Deliverability" application.   Work with your hoster if you are unsure about this.

AOL and Hotmail dump emails originating from server/client IP addresses that fail DNS reverse lookup. You should talk to your webhost to ensure that your webserver and hosting account / domain are properly configured with a PTR or DNS reverse lookup.

### Email Treated As Spam?

You might want to register your domain with [Google Postmaster Tools](https://postmaster.google.com/) to let it collect data about emails you send to recipients using Google's email platform, so that it can report to you any issues it detects with emails you're sending to them.

Also see [How do I prevent my email from being treated like spam?](/user/email/spam/).


