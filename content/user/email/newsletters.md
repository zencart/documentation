---
title: Newsletters 
description: Sending newsletters in Zen Cart 
category: email
weight: 10
---

Sending large numbers of emails (newsletters or other marketing content)
using [Send Email](/user/admin_pages/tools/send_email/) or 
[Newsletter Manager](/user/admin_pages/tools/newsletter/)
is not recommended.  Your server and hosting account probably don't allow for
mass quantities of broadcast emails, and doing so could cause you to be treated like a spammer. 

Instead, we recommend that you use an *Email Service Provider* (ESP) to handle your
bulk emailing needs.  See below for more information about using an ESP. 

### Exporting Email Addresses 
To export email addresses, use the [Email Address Exporter](https://www.zen-cart.com/downloads.php?do=file&id=6) plugin and use it to feed the emails into a 3rd-party provider.

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

### Admin Settings when using an Email Service Provider

Because you are no longer using Zen Cart's newsletter feature, you will want to stop capturing signups through Zen Cart.

- Turn off [Show Newsletter Checkbox](/user/admin_pages/configuration/configuration_customerdetails/#show_newsletter_checkbox) in Admin > Configuration > Customer Details. 

- Turn off [Display "Newsletter Unsubscribe" Link](/user/admin_pages/configuration/configuration_emailoptions/#display_newsletter_unsubscribe_link) in Admin > Configuration > E-Mail Options. 

### Handling Subscribes and Unsubscribes

Most Email Service Providers will provide you with a signup form to use on your website that allows you to allow people to signup for your newsletter.  Use this form, either as a [sidebox](/user/template/sideboxes/) or as a [new custom page](/user/customizing/add_pages/#build-a-new-custom-page). 

Generally unsubscribes will be done by clicking the unsubscribe link that is provided at the bottom of your email; doing this within your cart is somewhat complicated and will require custom coding.
 
