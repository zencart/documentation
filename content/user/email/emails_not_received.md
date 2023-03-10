---
title: Basic Email Troubleshooting
description: Emails are not being received - deliverability issues 
category: email
weight: 5 
---

## Testing Email 
The easiest way to test email from your cart is to create an account in your store using a non-free email address, and then finding that account in Admin > Customers > Customers, and using the _Email_ button on the right sidebar.

## Before you start testing
1. ALWAYS test on a NON-free email address.  Do not test with a yahoo, hotmail, msn, aol, etc address exclusively.  
1. You may need to test on multiple email addresses (by creating multiple store accounts) because some email services will drop email before even putting it in the junk folder. 
1. All email settings are shown in the screen [Admin > Configuration > Email](/user/admin_pages/configuration/configuration_email/). 

<hr>

### Symptom: Emails sent from the cart are not arriving

This is also called "undeliverable mail." You might see an error message that says something like "The mail server could not deliver mail to joe@example.com. The account or domain may not exist, they may be blacklisted, or missing the proper dns entries." 

Sometimes your mail server configuration requires a particular format in order to send messages.
Options to try include:

1. Enable `Emails Must Be Sent From Known Domain` so that the "From" address is set properly
1. Try a different Email Transport method](/user/email/email_transport_method/). 
Go to [Admin > Configuration > Email](/user/admin_pages/configuration/configuration_email/) and try them in this order: `php`, `smtp/smtpauth`, `sendmail`, `sendmail -f`. 
1. With SMTPAuth, you must enter your password in the _SMTP Email Account Password_ field.  Has your cPanel password changed recently?  If so, you may need to update the value in this field. 
1. Look on your hoster's control panel and see if you can add SPF and DKIM records yourself to increase your email reputation.  In cPanel, this is done using the "Email Deliverability" application.   Work with your hoster if you are unsure about this. See [SPF, DKIM and DMARC](/user/email/advanced_email_troubleshooting/#11-spf-dkim-and-dmarc) for more details. 
1. ALWAYS check to see whether a junk mail filter, spam block, or other blacklist system may have trapped your message before it could be delivered
1. Try enabling the [Email Archiving](/user/admin_pages/configuration/configuration_email/#email_archiving_active) feature. Then use the [Email Archive Manager](/user/email/email_archive_manager/) plugin to check and see whether Zen Cart really processed the email for sending. If it did, then the problem is related to how PHP is processing your messages after they leave Zen Cart. 
1. If the issue is arising from one particular customer, ask them to whitelist email from your domain.  For very strict filters, sometimes this is the only way to get through. 
1. Check if the customer's [email address is mis-typed](/user/running/mistyped_email/). 
1. Look for debug logs in the `/logs` folder.   Logs for email failures are named with the prefix `myDEBUG-bounced-email-adm-` for admin created emails, and `myDEBUG-bounced-email-` for storefront emails.

### Symptom: Email FROM-ADDRESS shows up funny
If your "FROM" email addresses contain extra brackets ")", this is due to having an incorrectly-formed email address defined in your store `Email Address (sent FROM)` setting.

### Symptom: Contact-Us emails aren't arriving

1. the Email From address may be malformed
1. the Contact Us Pulldown contents may not be formatted properly. Note the required syntax next to the input field.
1. Check if the customer's [email address is mis-typed](/user/running/mistyped_email/). 

## Further Email Troubleshooting

* [Diagnosing Email Problems](/user/email/email_introduction/#diagnosing-problems)

* [Advanced Email Troubleshooting](/user/email/advanced_email_troubleshooting/)

* [PHPMailer Troubleshooting Guide](https://github.com/PHPMailer/PHPMailer/wiki/Troubleshooting)

