---
title: Newsletters 
description: Sending newsletters in Zen Cart 
category: email
weight: 10
---

Sending large numbers of emails (newsletters or other marketing content)
using [Send Email](/user/admin_pages/tools/send_email/) or 
[Newsletter Manager](/user/admin_pages/tools/newsletter/)
with your regular email method - as specified in [EMAIL_TRANSPORT](/user/admin_pages/configuration/configuration_email/) - 
is not recommended.  Your server and hosting account probably don't allow for
mass quantities of broadcast emails, and doing so could cause you to be treated like a spammer. 

Instead, we recommend that you use an *Email Service Provider* (ESP) to handle your
bulk emailing needs.  See below for more information about using an ESP. 

For Newsletter Manager, another alternative exists in Zen Cart 1.5.8 and above.  You may continue using the Newsletter Manager, but use a different email transport method so your own host is not sending the emails.  See below for more information on this.

# Using an Email Service Provider 

### MailChimp
There are several alternatives for sending newsletters and mass marketing messages.
The best known service that has a free pricing level is MailChimp. 
With them you can send emails, generate reports, do automation and more. 
They offer a few pre-built templates and their free service is sufficient for most small sites. 
They also have paid features and now position themselves as a full marketing platform.

A [MailChimp Integration](https://www.zen-cart.com/downloads.php?do=file&id=425) plugin is available for Zen Cart. 


### MailChimp Alternatives 
Other providers exist as well, but you will need to do your own integration. 

Some names you might have heard of are Constant Contact, SendInBlue, and Sendy. 

If you want to look for other options, do a web search for "newsletter provider service."

### Hosting Requirements
With the current emphasis on [SPF, DKIM, and DMARC](/user/email/advanced_email_troubleshooting/#11-spf-dkim-and-dmarc) to verify your site's emails, you may be required to add a couple of extra settings in your site's DNS to include your Email Service Provider.  Especially if your email is hosted other than at MailChimp or one of its alternatives/competitors.  Without this setting you will probably receive a multitude of bounces.  Unfortunately, those bounces may not be reported to you or your customer.  If your Email Service Provider does not provide this setting, you will most likely have problems reaching all your customers with your latest promotion.

This setting tells the recipient that MailChimp or its alternative has "permission" to send emails using your email host and address.  It is generally in the form of a TXT entry with the name having an identifier something like k2.\_domainkey.yoursite.com or mail.\_domainkey.yoursite.com.  Your email service provider should have information if you search for "setup email domain authentication."  Current MailChimp instructions are available [here](https://mailchimp.com/help/set-up-email-domain-authentication/).The record itself will be a rather large string of text and may need to be added by your host if you are unable to add TXT settings to your site's DNS.  If you are able to make the entry yourself, make sure you accurately copy the information provided by your Email Service Provider.

### Admin Settings when using an Email Service Provider
Because you are no longer using Zen Cart's newsletter feature, you will want to stop capturing signups through Zen Cart.

- Turn off [Show Newsletter Checkbox](/user/admin_pages/configuration/configuration_customerdetails/#show_newsletter_checkbox) in Admin > Configuration > Customer Details. 

- Turn off [Display "Newsletter Unsubscribe" Link](/user/admin_pages/configuration/configuration_email/#display_newsletter_unsubscribe_link) in Admin > Configuration > Email. 

### Handling Subscribes and Unsubscribes
Most Email Service Providers will provide you with a signup form to use on your website that allows you to allow people to signup for your newsletter.  Use this form, either as a [sidebox](/user/template/sideboxes/) or as a [new custom page](/user/customizing/add_pages/#build-a-new-custom-page). 

Generally unsubscribes will be done by clicking the unsubscribe link that is provided at the bottom of your newsletter; doing this within your cart is somewhat complicated and will require custom coding.
 
### Exporting Email Addresses 
You will need to populate your subscriber list in whatever email service provider you choose.

To export email addresses, use the [Email Address Exporter](https://www.zen-cart.com/downloads.php?do=file&id=6) plugin and use it to feed the emails into a 3rd-party provider.

# Using the Newsletter SMTP Email settings 

In Zen Cart 1.5.8 and above, the page [Admin > Configuration > Email](/user/admin_pages/configuration/configuration_email/) has the following new values: 

- Newsletter SMTP Email Account Mailbox
- Newsletter SMTP Email Account Password
- Newsletter SMTP Email Mail Host
- Newsletter SMTP Email Mail Server Port
- Newsletter Modules 

Any of the pages listed in `Newsletter Modules` will use the values configured in these fields for sending email, so you can use the Zen Cart tools to build your email but an [External SMTP Server](/user/email/external_smtp_servers/) to send them. 

