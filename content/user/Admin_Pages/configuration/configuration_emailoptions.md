---
title: Configuration-E-Mail Options
description: Zen Cart Configuration-E-Mail Options Admin Page 
category: admin_pages
weight: 100
---

<b>E-Mail Transport Method</b>

<div class='indent'>Defines the method for sending mail.<br /><strong>PHP</strong> is the default, and uses built-in PHP wrappers for processing.<br />Servers running on Windows and MacOS should change this setting to <strong>SMTP</strong>.<br /><br /><strong>SMTPAUTH</strong> should only be used if your server requires SMTP authorization to send messages. You must also configure your SMTPAUTH settings in the appropriate fields in this admin section.<br /><br /><strong>sendmail</strong> is for linux/unix hosts using the sendmail program on the server<br /><strong>"sendmail-f"</strong> is only for servers which require the use of the -f parameter to send mail. This is a security setting often used to prevent spoofing. Will cause errors if your host mailserver is not configured to use it.<br /><br /><strong>Qmail</strong> is used for linux/unix hosts running Qmail as sendmail wrapper at /var/qmail/bin/sendmail.</div>


<b>Send E-Mails</b>

<div class='indent'>Send out e-mails?<br>Normally this is set to true.<br>Set to false to suppress ALL outgoing email messages from this store, such as when working with a test copy of your store offline.</div>


<b>E-Mail Linefeeds</b>

<div class='indent'>Defines the character sequence used to separate mail headers.</div>


<b>Enable HTML Emails?</b>

<div class='indent'>Send emails in HTML format if recipient has enabled it in their preferences.</div>


<b>Email Archiving Active?</b>

<div class='indent'>If you wish to have email messages archived/stored when sent, set this to "true".</div>


<b>E-Mail Friendly-Errors</b>

<div class='indent'>Do you want to display friendly errors if emails fail?  Setting this to false will display PHP errors and likely cause the script to fail. Only set to false while troubleshooting, and true for a live shop.</div>


<b>Email Address (Displayed to Contact you)</b>

<div class='indent'>Email address of Store Owner.  Used as "display only" when informing customers of how to contact you.</div>


<b>Email Address (sent FROM)</b>

<div class='indent'>Address from which email messages will be "sent" by default. Can be over-ridden at compose-time in admin modules.</div>


<b>Emails must send from known domain?</b>

<div class='indent'>Does your mailserver require that all outgoing emails have their "from" address match a known domain that exists on your webserver?<br /><br />This is often required in order to prevent spoofing and spam broadcasts.  If set to Yes, this will cause the email address (sent FROM) to be used as the "from" address on all outgoing mail.</div>


<b>Email Admin Format?</b>

<div class='indent'>Please select the Admin extra email format (Note: Enable HTML Emails must be on for HTML option to work)</div>


<b>Send Copy of Order Confirmation Emails To</b>

<div class='indent'>Send COPIES of order confirmation emails to the following email addresses, in this format: Name 1 &lt;email@address1&gt;, Name 2 &lt;email@address2&gt;</div>


<b>Send Copy of Create Account Emails To - Status</b>

<div class='indent'>Send copy of Create Account Status<br />0= off 1= on</div>


<b>Send Copy of Create Account Emails To</b>

<div class='indent'>Send copy of Create Account emails to the following email addresses, in this format: Name 1 &lt;email@address1&gt;, Name 2 &lt;email@address2&gt;</div>


<b>Send Copy of Customer GV Send Emails To - Status</b>

<div class='indent'>Send copy of Customer GV Send Status<br />0= off 1= on</div>


<b>Send Copy of Customer GV Send Emails To</b>

<div class='indent'>Send copy of Customer GV Send emails to the following email addresses, in this format: Name 1 &lt;email@address1&gt;, Name 2 &lt;email@address2&gt;</div>


<b>Send Copy of Admin GV Mail Emails To - Status</b>

<div class='indent'>Send copy of Admin GV Mail Status<br />0= off 1= on</div>


<b>Send Copy of Customer Admin GV Mail Emails To</b>

<div class='indent'>Send copy of Admin GV Mail emails to the following email addresses, in this format: Name 1 &lt;email@address1&gt;, Name 2 &lt;email@address2&gt;</div>


<b>Send Copy of Admin Discount Coupon Mail Emails To - Status</b>

<div class='indent'>Send copy of Admin Discount Coupon Mail Status<br />0= off 1= on</div>


<b>Send Copy of Customer Admin Discount Coupon Mail Emails To</b>

<div class='indent'>Send copy of Admin Discount Coupon Mail emails to the following email addresses, in this format: Name 1 &lt;email@address1&gt;, Name 2 &lt;email@address2&gt;</div>


<b>Send Copy of Admin Orders Status Emails To - Status</b>

<div class='indent'>Send copy of Admin Orders Status Status<br />0= off 1= on</div>


<b>Send Copy of Admin Orders Status Emails To</b>

<div class='indent'>Send copy of Admin Orders Status emails to the following email addresses, in this format: Name 1 &lt;email@address1&gt;, Name 2 &lt;email@address2&gt;</div>


<b>Send Notice of Pending Reviews Emails To - Status</b>

<div class='indent'>Send copy of Pending Reviews Status<br />0= off 1= on</div>


<b>Send Notice of Pending Reviews Emails To</b>

<div class='indent'>Send copy of Pending Reviews emails to the following email addresses, in this format: Name 1 &lt;email@address1&gt;, Name 2 &lt;email@address2&gt;</div>


<b>Set "Contact Us" Email Dropdown List</b>

<div class='indent'>On the "Contact Us" Page, set the list of email addresses , in this format: Name 1 &lt;email@address1&gt;, Name 2 &lt;email@address2&gt;</div>


<b>Contact Us - Show Store Name and Address</b>

<div class='indent'>Include Store Name and Address<br />0= off 1= on</div>


<b>Send Low Stock Emails</b>

<div class='indent'>When stock level is at or below low stock level send an email<br />0= off<br />1= on</div>


<b>Send Low Stock Emails To</b>

<div class='indent'>When stock level is at or below low stock level send an email to this address, in this format: Name 1 &lt;email@address1&gt;, Name 2 &lt;email@address2&gt;</div>


<b>Display "Newsletter Unsubscribe" Link?</b>

<div class='indent'>Show "Newsletter Unsubscribe" link in the "Information" side-box?</div>


<b>Audience-Select Count Display</b>

<div class='indent'>When displaying lists of available audiences/recipients, should the recipients-count be included? <br /><em>(This may make things slower if you have a lot of customers or complex audience queries)</em></div>


<b>SMTP Email Account Mailbox</b>

<div class='indent'>Enter the mailbox account name (me@mydomain.com) supplied by your host. This is the account name that your host requires for SMTP authentication.<br />Only required if using SMTP Authentication for email.</div>


<b>SMTP Email Account Password</b>

<div class='indent'>Enter the password for your SMTP mailbox. <br />Only required if using SMTP Authentication for email.</div>


<b>SMTP Email Mail Host</b>

<div class='indent'>Enter the DNS name of your SMTP mail server.<br />ie: mail.mydomain.com<br />or 55.66.77.88<br />Only required if using SMTP Authentication for email.</div>


<b>SMTP Email Mail Server Port</b>

<div class='indent'>Enter the IP port number that your SMTP mailserver operates on.<br />Only required if using SMTP Authentication for email.<br><br>Default: 25<br>Typical values are:<br>25 - normal unencrypted SMTP<br>587 - encrypted SMTP<br>465 - older MS SMTP port</div>


<b>Convert currencies for Text emails</b>

<div class='indent'>What currency conversions do you need for Text emails?<br />Example = &amp;pound;,&pound;:&amp;euro;,&euro;</div>


