---
title: Using External SMTP Servers 
description: Letting someone else handle your Zen Cart email
category: email
weight: 10
---

## Using external SMTP mail servers

Some people prefer to use resources such as Gmail or Yahoo! Mail for sending their business emails. There are differing schools of thought about the merits of doing so. If you deem that this is the best practice for your business, the following information may be of help to you.

**NOTE:** If you are self-hosting on a local PC server for development purposes, remember that your ISP (internet provider) usually blocks outgoing traffic on port 25, which is commonly used for email. Anything on port 25 destined for any server other than the ISP's own email server is generally blocked in order to control spam. You will need to choose another port (usually 587 or sometimes 465) and use SMTPAUTH and specify the correct SMTP server credentials.

See here: for a [list of common server SMTP addresses](http://www.arclab.com/products/amlc/list-of-smtp-and-pop3-servers-mailserver-list.html) if you're using a "free" email service. 

**Note:** Many customers prefer that you have a legitimate email address matching your domain name, not something like "billys-store@gmail.com" which is rather less authentic-looking. Build credibility with your customers by getting proper email addresses to match your domain name!

### SMTP over SSL

If your host requires that you send email over SSL, then be sure to set your SMTP Port to 465.

### SMTP over TLS

TLS is the modern preferred method for secure email transfer. But some hosts still haven't configured their servers for TLS properly, so you may have to use the old SSL approach above.

To use TLS, simply set your port to 587.

In rare cases you may need to get really technical and also specify your TLS/SSL Certificate by adding a define for 'SMTPAUTH_EMAIL_CERTIFICATE_CONTEXT' in the extra_datafiles folder to supply your certificate-context, and in that same file also define SMTPAUTH_EMAIL_PROTOCOL to 'starttls'. This is arguably more complicated and should be considered a last resort. Definitely try to sort out your email issues with your host before attempting StartTLS configuration!

### Yahoo Hosting

If you are using Yahoo as a webhost, doing a search in the Yahoo help pages for PHP/Perl set up may help. Also setting up a tmp file in your Yahoo account may shed a bunch of light on things and give you answers right away as to why the e-mail isn't sending.

1.  In your Yahoo control panel, check if the email address you are using is set as "Pop/Webmail", and not just "Mail Administrator". You may have to create a new one.
2.  The Zen Cart option **Emails must send from known domain** must be set to YES, and mail transport should be SMTPAUTH.
3.  Yahoo Outgoing (SMTP) Mail Server: smtp.mail.yahoo.com
4.  SMTP Port 465 (You MIGHT be able to use 587 or 25, but may have to check with tech support first.)

If you're hosting someplace other than Yahoo but trying to send email through your Yahoo email address, work with your hosting company to configure your DomainKeys and SPF settings to allow the emails to be accepted instead of being rejected as forged spam messages.

### Google Mail / Gmail

Gmail / Google Apps Mail requires that your email communications occur over a secure channel, which means you need to send on port 587 for TLS. The latest version of Zen Cart supports this by using the following settings in Admin > Configuration > Email Options:

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

**Note:** To use email (eg SMTPAUTH) with a Google mail account you need to enable "allow less secure authentication" inside your google account settings. (This name sounds much worse than it is; it's still secure.) 

Instructions on allowing less secure apps to use your account are provided [here](https://support.google.com/accounts/answer/6010255?hl=en). 

More technical information is available in [Google's Help Center](http://mail.google.com/support/bin/answer.py?answer=13287).

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

