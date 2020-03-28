---
title: TroubleShooting Email - Advanced Part II
description: Zen Cart TroubleShooting Email - Advanced Part II
category: email
weight: 10
---

Zen Cart's email infrastructure is largely dependent on the services available to the computer operating as your webserver. This includes internet connection issues, available ports, as well as PHP configuration options and the programs/services running on your server.

## Zen Cart Email Infrastructure Explained

Here's how it works:

1.  _Admin_ and _Store_ both use the same infrastructure.
2.  Zen Cart uses PHPMailer for sending mail.
3.  Wherever an email is sent, it is initiated via `zen_mail()` which is in the `includes/functions/functions_email.php`. This builds the email object according to all your settings in Admin > Config > Email options.
    *   transport method: PHP, smtp, sendmail, sendmail-f, smtpauth, etc.
    *   text-only vs HTML formatted
    *   sent to, sendfrom
    *   ... everything from that section, really.
4.  Then it hands the email off to PHPMailer to send it.
    *   If the transport is SMTP/SMPTAUTH, then direct communication with the specified mailserver is initiated. **SMTPAUTH IS THE RECOMMENDED TRANSPORT.**
    *   If the transport is "PHP", then the server's PHP configuration takes over entirely, using whatever PHP has been configured to use in the server's php.ini settings.
    *   If the transport is a sendmail function, then the server attempts to use the sendmail program on your webserver.
5.  If email archiving is enabled and no error message is encountered (ie: the email is delivered without being rejected by the sending server), the email is stored to the archive table.
6.  If an error occurs, then the error details are logged into the /logs/ folder as "myDEBUG-xxxxxx.log" files.  
See [reading a myDEBUG log](/user/troubleshooting/debug_logs/). 

Done.

That's it.

## Prerequisites

1.  Your webserver must have a mail service enabled. For Linux/Unix hosts, this is typically done via sendmail or exim or qmail daemons. On Windows™ servers, this may be done via services offered with IIS.
2.  Your webserver must allow email connections from PHP.
3.  If you are using sendmail options, then the PHP configuration for sendmail functions must be configured properly on the server.
4.  You must have an unrestricted connection to the mailserver you're sending through.
    *   If you are running from a home-based server (ie: for testing), note that your ISP may automatically have port 25 blocked so that you have to send mail through their server. In this case, use SMTP for your transport method, and supply your ISP's mailserver as your SMTP host.
    *   If your webhost mailserver is reachable on another port, supply that port number in the SMTP settings.

## Diagnosing Problems

1.  change transport methods (ask your host what's best ... they should know how they've configured your server).
    *   **NOTE:** `SMTPAUTH` is least likely to end up getting treated as spam.
2.  change send-from email addresses (Admin->Configuration->Email Options). This should be an email associated with your server's domain. Preferably not a "free email account" such as Gmail, since your server is *not* a Gmail server and therefore your emails would be seen as spammy impersonation attempts, unless you're using SMTPAUTH properly configured for your account.
    *   MAKE SURE THE ADDRESS IS VALID.
    *   It is recommended to use an email account linked to the same domain name as your store. Attempting to masquerade with a different email address makes your emails prime candidates for being treated as junkmail, and thus not delivered.
3.  change send-to email addresses ... DO NOT TEST USING FREE MAIL SERVICES ... your mail is often dropped to a junkmail black hole.
4.  be sure there are no embedded carriage returns in your send-to email addresses (see [https://www.zen-cart.com/showthread.php?t=86423](https://www.zen-cart.com/showthread.php?t=86423) for details)
5.  check your junkmail settings.
6.  research whether your mailserver or hosting company is blacklisted (you can check [http://www.mxtoolbox.com/blacklists.aspx](http://www.mxtoolbox.com/blacklists.aspx) or google for _smtp blacklist_ for additional resources)
7.  try setting the option for **Emails must send from known domain?** to true. This causes the email "sender" address to be more aligned to your own website, and thus less likely to be rejected while processing. This should always be set to true nowadays.
8.  try testing with HTML emails OFF, since many spam filters block HTML-formatted messages before they even get out the gate.
9.  check the mailserver logs ... is it complaining about something, either inbound or outbound?
10.  for kicks, get the webserver/mailserver rebooted and dump all the logs ... just maybe something's runamuck in there ...
11.  Try enabling Email Archiving (Admin->Configuration->Email Options->Email Archiving). Then install the [email archive manager](https://www.zen-cart.com/downloads.php?do=file&id=101) from the Zen Cart Downloads section (in admin tools), and confirm that the emails are actually being sent from Zen Cart. If it's in the archive, it was handed off to the mailserver. Once the email leaves Zen Cart, it's at the mercy of your mailserver.
12.  Look at your raw/full email headers. Does the "from" address appear to be a "nobody@xxxxxxx" address? Some hosts block these. The "email must send from known domain" setting is designed to counteract this. The SMTPAUTH setting also helps to work around this.
13.  This is RARE: If using "sendmail" and your "sendmail" path on your webserver is not the default of /usr/sbin/sendmail then you can override the default by adding a definition for it in a new file on your server: /includes/extra_datafiles/email_sendmail_override.php ... create a define for EMAIL_SENDMAIL_PATH and point it to the actual sendmail path for your particular host. This should not be necessary, and usually using "PHP" as transport method will correct it without making this edit.
14.  Also rare: Does your server require 7bit mail encoding instead of the default 8bit? If so, edit the /includes/extra_configures.email_use_8bit.php file and put // before the define statement there.

If the email doesn't get to its destination, then usually the problem is a misconfiguration of the MTA or the host is blacklisted somewhere, or ports are blocked or ... well ... the probable causes are for a system administrator to understand.

**For IN DEPTH ASSISTANCE on email matters, see [Advanced Email Troubleshooting I](/user/email/advanced_email_troubleshooting_1/)**

### Advanced Email Debugging

If you are troubleshooting problems with SMTP or SMTPAUTH and want to see the exact responses from the SMTP server handshake, you can do the following to cause the email server conversation to be displayed on-screen during delivery. THIS IS ABSOLUTELY UNSUITABLE FOR USE ON A LIVE STORE because visitors to your site have no business seeing any of the information displayed, and some of the information could be misused by those with malicious intent. USE WITH CAUTION!!!

To enable email-debug-output, create a PHP file at either of these locations, depending on whether you're testing email on the storefront side or on the admin side, respectively: `includes/extra_datafiles/email_debug.php` or `YOURADMIN/includes/extra_datafiles/email_debug.php`. 

The content of the file should be just one line:

<pre>
&lt;?php 
   define('EMAIL_SYSTEM_DEBUG','5');
</pre>

Then try sending another email. The SMTP handshake information will be dumped to the /logs/myDEBUG-xxxxxx.log folder/files if SMTP/SMTPAUTH is your transport method.

Be sure to delete that email_debug.php file when you're done testing; otherwise your store won't work properly because of the bizarre information that gets output to the screen!

### Troubleshooting Questions for your Hosting Company

Have you asked your hosting company what the right configuration is for your server to send mail most appropriately?

As far as Zen Cart is concerned, you have these options. Ask your host what they require:

1.  Mail Transport ... best to use SMTPAUTH, and supply your mailbox credentials in the SMTP settings
2.  Emails must send from known domain ... true/false (ie: does the server accept emails that have "from headers" set to external domains, or only it's own domains?) Best to set to true.
3.  SMTP port to use ... 25, or 587 for TLS, or sometimes 465 for old SSL mode.

If your "contact us" emails are not arriving at the desired destinations, try emptying the "contact us pulldown" list. This will force it to use your Store Owner email address and bypass the occasional confusion encountered with properly formatting addresses for the pulldown list.

As mentioned earlier, if the emails are showing in the archive log (assuming you've enabled it), then Zen Cart is generating the message and handing it off to your webserver to send. If it's not being delivered, then either your webserver is dumping it, or the recipient is not getting it, possibly due to frequent spam from your webhost or other reasons. **Perhaps your hosting company will offer you some assistance or at least explain how their servers are configured so that you can determine the right setting for your hosting environment. They know your server better than anyone.**

Ask your host whether your/their mailserver is blacklisted by anyone. If so, try to get the blacklisting removed.

Is your account's SPF record correct? DKIM?

AOL and Hotmail dump emails originating from server/client IP addresses that fail DNS reverse lookup. You should talk to your webhost to ensure that your webserver and hosting account / domain are properly configured with a PTR or DNS reverse lookup.

## Using external SMTP mail servers

Some people prefer to use resources such as Gmail or Yahoo! Mail for sending their business emails. There are differing schools of thought about the merits of doing so. If you deem that this is the best practice for your business, the following information may be of help to you.

**NOTE:** If you are self-hosting on a local PC server for development purposes, remember that your ISP (internet provider) usually blocks outgoing traffic on port 25, which is commonly used for email. Anything on port 25 destined for any server other than the ISP's own email server is generally blocked in order to control spam. You will need to choose another port (usually 587 or sometimes 465) and use SMTPAUTH and specify the correct SMTP server credentials.

See here: for[a list of common server SMTP addresses](http://www.arclab.com/products/amlc/list-of-smtp-and-pop3-servers-mailserver-list.html) if you're using a "free" email service. (Note: many customers prefer that you have a legitimate email address matching your domain name, not something like "billys-store@gmail.com" which is rather less authentic-looking. Build credibility with your customers by getting proper email addresses to match your domain name!!!!)

### SMTP over SSL

If your host requires that you send email over SSL, then be sure to set your SMTP Port to 465\.

### SMTP over TLS

TLS is the modern preferred method for secure email transfer. But some hosts still haven't configured their servers for TLS properly, so you may have to use the old SSL approach above.

To use TLS, simply set your port to 587.

In rare cases you may need to get really technical and also specify your TLS/SSL Certificate by adding a define for 'SMTPAUTH_EMAIL_CERTIFICATE_CONTEXT' in the extra_datafiles folder to supply your certificate-context, and in that same file also define SMTPAUTH_EMAIL_PROTOCOL to 'starttls'. This is arguably more complicated and should be considered a last resort. Definitely try to sort out your email issues with your host before attempting StartTLS configuration!!!!

### Yahoo Hosting

If you are using Yahoo as a webhost, doing a search in the Yahoo help pages for PHP/Perl set up may help. Also setting up a tmp file in your Yahoo account may shed a bunch of light on things and give you answers right away as to why the e-mail isn't sending.

1.  In your Yahoo control panel, check if the email address you are using is set as "Pop/Webmail", and not just "Mail Administrator". You may have to create a new one.
2.  The Zen Cart option **Emails must send from known domain** must be set to YES, and mail transport should be SMTPAUTH.
3.  Yahoo Outgoing (SMTP) Mail Server: smtp.mail.yahoo.com
4.  SMTP Port 465 (You MIGHT be able to use 587 or 25, but may have to check with tech support first.)

If you're hosting someplace other than Yahoo but trying to send email through your Yahoo email address, work with your hosting company to configure your DomainKeys and SPF settings to allow the emails to be accepted instead of being rejected as forged spam messages.

### Google Mail / Gmail

Gmail / Google Apps Mail requires that your email communications occur over a secure channel, which means you need to send on port 587 for TLS. The latest version of Zen Cart supports this by using the following settings in Admin->Configuration->Email Options:

#### Gmail

*   Email Transport: Gmail
*   SMTP Username: your gmail username
*   SMTP Password: your gmail password
*   SMTP Host: smtp.gmail.com
*   SMTP Port 587

#### Google Apps Mail

*   Email Transport: SMTPAUTH
*   SMTP Username: your google-apps-mail username
*   SMTP Password: your google-apps-mail password
*   SMTP Host: smtp.gmail.com
*   SMTP Port 587

More technical information is available in [Google's Help Center](http://mail.google.com/support/bin/answer.py?answer=13287)

You may have to have your host make some changes to your domain's MX records if you are using Google hosted mail. Details for that are on Google's help site.

You may also have to open your webserver's firewall to allow access to Google's servers and whatever port you're using to communicate with them. Your hosting company's server administrator will know how to identify the correct address and how to fix their firewall accordingly.

### GoDaddy Hosting Plans

1.  If using the default "PHP" setting for Email Transport method doesn't work, try the following:
    *   Use "SMTP" for your Email Transport setting instead.
    *   Set your SMTP Email Server address to: **relay-hosting.secureserver.net**, and the Mail Server Port to **25**
    *   GoDaddy's odd configuration usually requires that you leave the SMTP mailbox and password fields blank. (Alternatively use enter your email address as the mailbox, and supply the corresponding password.)
    *   Set the "Emails must send from known domain" to yes. (This is required so that the GD mail servers don't reject your emails)
    *   For your "Sent FROM" email address, use an email address that matches the domain name of your website. ie: if your website is www.abc.com, then use something like sales@abc.com as your Sent From email address (otherwise GD may reject your emails).
    *   Do not send an email "to yourself", "from yourself" when testing.
2.  Set your Max Email limit:
    *   If you have a GoDaddy hosting plan and plan to use it for sending emails from your Zen Cart site, you should check your email account list and set the "smtp relay transmissions per day" to the max of 250/day instead of the default of 0/day.

## Preventing My Mail From Being Treated as Spam

The most common cause of email being treated as spam stems from how your **webserver** is configured to send mail. By default, emails sent with the Transport set to PHP will appear as a user called "nobody@yourdomain.com" or something similar. Most spam filters will look at that and assume that those emails were generated by spam bots and thus the message is dumped without any further consideration.

Other causes include messages which have ALL UPPERCASE letters in their Subject field. Don't do that. You can usually set the subject line for individual emails in your Zen Cart language files.

1.  change your email transport method to "SMTPAUTH" (or "sendmail -f" as a last resort). This will cause the messages to appear as they are coming from "you" instead of as coming from your server's unsigned PHP.
2.  the option 'Emails must send from known domain?' should be set to True. This will cause e-mail providers see that it is coming from someplace legitimate and not filter it as spam. And, more specifically, your own webserver will not ignore it because it will now appear as legitimately coming from itself (whom it "knows"), rather than from a 3rd-party.
3.  AOL and Hotmail dump emails originating from server/client IP addresses that fail DNS reverse lookup. You should talk to your webhost to ensure that your webserver and hosting account / domain are properly configured with a PTR or DNS reverse lookup. If those words/terms don't mean anything to you, simply talk to your hosting company about them!

## HTML-formatted Email in non-English Languages

The english HTML emails are built from the files in the /email folder. If you have other languages, you'll need to create your own HTML email template files and put them into subfolders named according to the 2-letter language code.

ie:

*   /email/de/
*   /email/es/
*   /email/fr/

## Why Do Emails Not Show in HTML format?

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

Be sure to review the "Diagnosing Problems" section above for other tips related to potential delivery problems.

