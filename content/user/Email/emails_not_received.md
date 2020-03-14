---
title: Emails are not received or sending
category: email
weight: 1
---
## Emails Are Not Arriving
Sometimes your mail server configuration requires a particular format in order to send messages.
Options to try include:

1. Enable `Emails Must Be Sent From Known Domain` so that the "From" address is set properly
1. Try a different Email Transport method.  Try "php".  If you're using "sendmail", try "sendmail -f".  If you're using SMTP, try SMTPAUTH.
1. ALWAYS test on a NON-free email address.  Do not test with a yahoo, hotmail, msn, aol, etc address exclusively.
1. ALWAYS check to see whether a junk mail filter, spam block, or other blacklist system may have trapped your message before it could be delivered
1. Try enabling the Email Archiving feature. (Note: this can chew up server database disk space quickly.) Then use the Email Archive Viewer contribution to check and see whether Zen Cart really processed the email for sending. If it did, then the problem is related to how PHP is processing your messages after they leave Zen Cart. 

## Email Transport methods explained
Have you selected the appropriate "Email Transport" method for your webserver?  (Admin->Configuration->Email Options)
Suggest trying them in this order:

1. "php" -- this uses whatever email method your webserver is configured to use for PHP mail commands, as set by your webhost.  This will work fine in most cases.
1. "smtp" or "smtpauth" -- for reliable email, many hosts require that you use "smtp" or usually "smtpauth" and set all the SMTP settings shown lower on the page.
1. "sendmail" -- if "php" doesn't work and you're not running a windows server, this is your next likely choice.
1. "sendmail -f" -- this is ideal in cases where your webserver configuration has some tighter security requirements -- esp in busy shared-hosting environments.


## Email FROM-ADDRESS Shows Up Funny
If your "FROM" email addresses contain extra brackets ")", this is due to having an incorrectly-formed email address defined in your store `EMAIL_FROM` setting.

Contact-Us emails aren't arriving
a. the Email From address may be malformed

b. the Contact Us Pulldown contents may not be formatted properly. Note the required syntax next to the input field.


