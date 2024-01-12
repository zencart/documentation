---
title: Configuration ≫ Email
category: admin_pages
weight: 100 
---

<h2 id="email_transport_method">E-Mail Transport Method</h2>

<div class='indent'>Key: <b>EMAIL_TRANSPORT</b><br />
Path: <b>Configuration > Email</b><br />
Description: Defines the method for sending mail.<br><br><strong>PHP</strong> is the default, and uses built-in PHP wrappers for processing.<br><strong>smtpauth</strong> should be used by most sites, as it provides secure sending of authenticated email. You must also configure your smtpauth settings in the appropriate fields in this admin section.<br><strong>Gmail</strong> is used for sending emails using the Google mail service, and requires the [less secure] setting enabled in your gmail account.<br><strong>sendmail</strong> is for linux/unix hosts using the sendmail program on the server<br><strong>sendmail-f</strong> is only for servers which require the use of the -f parameter to use sendmail. This is a security setting often used to prevent spoofing. Will cause errors if your host mailserver is not configured to use it.<br><strong>Qmail</strong> is used for linux/unix hosts running Qmail as sendmail wrapper at /var/qmail/bin/sendmail.<br><br>MOST SITES WILL USE [smtpauth].</div>


<h2 id="send_emails">Send E-Mails</h2>

<div class='indent'>Key: <b>SEND_EMAILS</b><br />
Path: <b>Configuration > Email</b><br />
Description: Send out e-mails?<br>Normally this is set to true.<br>Set to false to suppress ALL outgoing email messages from this store, such as when working with a test copy of your store offline.</div>


<h2 id="enable_html_emails">Enable HTML Emails?</h2>

<div class='indent'>Key: <b>EMAIL_USE_HTML</b><br />
Path: <b>Configuration > Email</b><br />
Description: Send emails in HTML format if recipient has enabled it in their preferences.</div>


<h2 id="email_archiving_active">Email Archiving Active?</h2>

<div class='indent'>Key: <b>EMAIL_ARCHIVE</b><br />
Path: <b>Configuration > Email</b><br />
Description: If you wish to have email messages archived/stored when sent, set this to "true".</div>


<h2 id="email_address_displayed_to_contact_you">Email Address (Displayed to Contact you)</h2>

<div class='indent'>Key: <b>STORE_OWNER_EMAIL_ADDRESS</b><br />
Path: <b>Configuration > Email</b><br />
Description: Email address of Store Owner.  Used as "display only" when informing customers of how to contact you.</div>


<h2 id="email_address_sent_from">Email Address (sent FROM)</h2>

<div class='indent'>Key: <b>EMAIL_FROM</b><br />
Path: <b>Configuration > Email</b><br />
Description: Address from which email messages will be "sent" by default. Can be over-ridden at compose-time in admin modules.</div>


<h2 id="emails_must_send_from_known_domain">Emails must send from known domain?</h2>

<div class='indent'>Key: <b>EMAIL_SEND_MUST_BE_STORE</b><br />
Path: <b>Configuration > Email</b><br />
Description: Does your mailserver require that all outgoing emails have their "from" address match a known domain that exists on your webserver?<br /><br />This is often required in order to prevent spoofing and spam broadcasts.  If set to Yes, this will cause the email address (sent FROM) to be used as the "from" address on all outgoing mail.</div>


<h2 id="email_admin_format">Email Admin Format?</h2>

<div class='indent'>Key: <b>ADMIN_EXTRA_EMAIL_FORMAT</b><br />
Path: <b>Configuration > Email</b><br />
Description: Please select the Admin extra email format (Note: Enable HTML Emails must be on for HTML option to work)</div>


<h2 id="send_copy_of_order_confirmation_emails_to">Send Copy of Order Confirmation Emails To</h2>

<div class='indent'>Key: <b>SEND_EXTRA_ORDER_EMAILS_TO</b><br />
Path: <b>Configuration > Email</b><br />
Description: Send COPIES of order confirmation emails to the following email addresses, in this format: Name 1 &lt;email@address1&gt;, Name 2 &lt;email@address2&gt;</div>


<h2 id="send_copy_of_create_account_emails_to__status">Send Copy of Create Account Emails To - Status</h2>

<div class='indent'>Key: <b>SEND_EXTRA_CREATE_ACCOUNT_EMAILS_TO_STATUS</b><br />
Path: <b>Configuration > Email</b><br />
Description: Send copy of Create Account Status<br />0= off 1= on</div>


<h2 id="send_copy_of_create_account_emails_to">Send Copy of Create Account Emails To</h2>

<div class='indent'>Key: <b>SEND_EXTRA_CREATE_ACCOUNT_EMAILS_TO</b><br />
Path: <b>Configuration > Email</b><br />
Description: Send copy of Create Account emails to the following email addresses, in this format: Name 1 &lt;email@address1&gt;, Name 2 &lt;email@address2&gt;</div>


<h2 id="send_copy_of_customer_gv_send_emails_to__status">Send Copy of Customer GV Send Emails To - Status</h2>

<div class='indent'>Key: <b>SEND_EXTRA_GV_CUSTOMER_EMAILS_TO_STATUS</b><br />
Path: <b>Configuration > Email</b><br />
Description: Send copy of Customer GV Send Status<br />0= off 1= on</div>


<h2 id="send_copy_of_customer_gv_send_emails_to">Send Copy of Customer GV Send Emails To</h2>

<div class='indent'>Key: <b>SEND_EXTRA_GV_CUSTOMER_EMAILS_TO</b><br />
Path: <b>Configuration > Email</b><br />
Description: Send copy of Customer GV Send emails to the following email addresses, in this format: Name 1 &lt;email@address1&gt;, Name 2 &lt;email@address2&gt;</div>


<h2 id="send_copy_of_admin_gv_mail_emails_to__status">Send Copy of Admin GV Mail Emails To - Status</h2>

<div class='indent'>Key: <b>SEND_EXTRA_GV_ADMIN_EMAILS_TO_STATUS</b><br />
Path: <b>Configuration > Email</b><br />
Description: Send copy of Admin GV Mail Status<br />0= off 1= on</div>


<h2 id="send_copy_of_customer_admin_gv_mail_emails_to">Send Copy of Customer Admin GV Mail Emails To</h2>

<div class='indent'>Key: <b>SEND_EXTRA_GV_ADMIN_EMAILS_TO</b><br />
Path: <b>Configuration > Email</b><br />
Description: Send copy of Admin GV Mail emails to the following email addresses, in this format: Name 1 &lt;email@address1&gt;, Name 2 &lt;email@address2&gt;</div>


<h2 id="send_copy_of_admin_discount_coupon_mail_emails_to__status">Send Copy of Admin Discount Coupon Mail Emails To - Status</h2>

<div class='indent'>Key: <b>SEND_EXTRA_DISCOUNT_COUPON_ADMIN_EMAILS_TO_STATUS</b><br />
Path: <b>Configuration > Email</b><br />
Description: Send copy of Admin Discount Coupon Mail Status<br />0= off 1= on</div>


<h2 id="send_copy_of_customer_admin_discount_coupon_mail_emails_to">Send Copy of Customer Admin Discount Coupon Mail Emails To</h2>

<div class='indent'>Key: <b>SEND_EXTRA_DISCOUNT_COUPON_ADMIN_EMAILS_TO</b><br />
Path: <b>Configuration > Email</b><br />
Description: Send copy of Admin Discount Coupon Mail emails to the following email addresses, in this format: Name 1 &lt;email@address1&gt;, Name 2 &lt;email@address2&gt;</div>


<h2 id="send_copy_of_admin_orders_status_emails_to__status">Send Copy of Admin Orders Status Emails To - Status</h2>

<div class='indent'>Key: <b>SEND_EXTRA_ORDERS_STATUS_ADMIN_EMAILS_TO_STATUS</b><br />
Path: <b>Configuration > Email</b><br />
Description: Send copy of Admin Orders Status Status<br />0= off 1= on</div>


<h2 id="send_copy_of_admin_orders_status_emails_to">Send Copy of Admin Orders Status Emails To</h2>

<div class='indent'>Key: <b>SEND_EXTRA_ORDERS_STATUS_ADMIN_EMAILS_TO</b><br />
Path: <b>Configuration > Email</b><br />
Description: Send copy of Admin Orders Status emails to the following email addresses, in this format: Name 1 &lt;email@address1&gt;, Name 2 &lt;email@address2&gt;</div>


<h2 id="send_notice_of_pending_reviews_emails_to__status">Send Notice of Pending Reviews Emails To - Status</h2>

<div class='indent'>Key: <b>SEND_EXTRA_REVIEW_NOTIFICATION_EMAILS_TO_STATUS</b><br />
Path: <b>Configuration > Email</b><br />
Description: Send copy of Pending Reviews Status<br />0= off 1= on</div>


<h2 id="send_notice_of_pending_reviews_emails_to">Send Notice of Pending Reviews Emails To</h2>

<div class='indent'>Key: <b>SEND_EXTRA_REVIEW_NOTIFICATION_EMAILS_TO</b><br />
Path: <b>Configuration > Email</b><br />
Description: Send copy of Pending Reviews emails to the following email addresses, in this format: Name 1 &lt;email@address1&gt;, Name 2 &lt;email@address2&gt;</div>


<h2 id="set_contact_us_email_dropdown_list">Set "Contact Us" Email Dropdown List</h2>

<div class='indent'>Key: <b>CONTACT_US_LIST</b><br />
Path: <b>Configuration > Email</b><br />
Description: On the "Contact Us" Page, set the list of email addresses , in this format: Name 1 &lt;email@address1&gt;, Name 2 &lt;email@address2&gt;</div>


<h2 id="contact_us__show_store_name_and_address">Contact Us - Show Store Name and Address</h2>

<div class='indent'>Key: <b>CONTACT_US_STORE_NAME_ADDRESS</b><br />
Path: <b>Configuration > Email</b><br />
Description: Include Store Name and Address<br />0= off 1= on</div>


<h2 id="send_low_stock_emails">Send Low Stock Emails</h2>

<div class='indent'>Key: <b>SEND_LOWSTOCK_EMAIL</b><br />
Path: <b>Configuration > Email</b><br />
Description: When stock level is at or below low stock level send an email<br />0= off<br />1= on</div>


<h2 id="send_low_stock_emails_to">Send Low Stock Emails To</h2>

<div class='indent'>Key: <b>SEND_EXTRA_LOW_STOCK_EMAILS_TO</b><br />
Path: <b>Configuration > Email</b><br />
Description: When stock level is at or below low stock level send an email to this address, in this format: Name 1 &lt;email@address1&gt;, Name 2 &lt;email@address2&gt;</div>


<h2 id="display_newsletter_unsubscribe_link">Display "Newsletter Unsubscribe" Link?</h2>

<div class='indent'>Key: <b>SHOW_NEWSLETTER_UNSUBSCRIBE_LINK</b><br />
Path: <b>Configuration > Email</b><br />
Description: Show "Newsletter Unsubscribe" link in the "Information" side-box?</div>


<h2 id="audienceselect_count_display">Audience-Select Count Display</h2>

<div class='indent'>Key: <b>AUDIENCE_SELECT_DISPLAY_COUNTS</b><br />
Path: <b>Configuration > Email</b><br />
Description: When displaying lists of available audiences/recipients, should the recipients-count be included? <br /><em>(This may make things slower if you have a lot of customers or complex audience queries)</em></div>


<h2 id="smtp_email_account_mailbox">SMTP Email Account Mailbox</h2>

<div class='indent'>Key: <b>EMAIL_SMTPAUTH_MAILBOX</b><br />
Path: <b>Configuration > Email</b><br />
Description: Enter the mailbox account name (me@mydomain.com) supplied by your host. This is the account name that your host requires for SMTP authentication.<br />Only required if using SMTP Authentication for email.</div>


<h2 id="smtp_email_account_password">SMTP Email Account Password</h2>

<div class='indent'>Key: <b>EMAIL_SMTPAUTH_PASSWORD</b><br />
Path: <b>Configuration > Email</b><br />
Description: Enter the password for your SMTP mailbox. <br />Only required if using SMTP Authentication for email.</div>


<h2 id="smtp_email_mail_host">SMTP Email Mail Host</h2>

<div class='indent'>Key: <b>EMAIL_SMTPAUTH_MAIL_SERVER</b><br />
Path: <b>Configuration > Email</b><br />
Description: Enter the DNS name of your SMTP mail server.<br />ie: mail.mydomain.com<br />or 55.66.77.88<br />Only required if using SMTP Authentication for email.</div>


<h2 id="smtp_email_mail_server_port">SMTP Email Mail Server Port</h2>

<div class='indent'>Key: <b>EMAIL_SMTPAUTH_MAIL_SERVER_PORT</b><br />
Path: <b>Configuration > Email</b><br />
Description: Enter the IP port number that your SMTP mailserver operates on.<br />Only required if using SMTP Authentication for email.<br><br>Default: 25<br>Typical values are:<br>25 - normal unencrypted SMTP<br>587 - encrypted SMTP<br>465 - older MS SMTP port</div>


<h2 id="convert_currencies_for_text_emails">Convert currencies for Text emails</h2>

<div class='indent'>Key: <b>CURRENCIES_TRANSLATIONS</b><br />
Path: <b>Configuration > Email</b><br />
Description: What currency conversions do you need for Text emails?<br />Example = &amp;pound;,&pound;:&amp;euro;,&euro;</div>


<h2 id="newsletter_smtp_email_account_mailbox">Newsletter SMTP Email Account Mailbox</h2>

<div class='indent'>Key: <b>NEWSLETTER_EMAIL_SMTPAUTH_MAILBOX</b><br />
Path: <b>Configuration > Email</b><br />
Description: Enter the newsletter mailbox account name (me@mydomain.com) supplied by your host. This is the account name that your newsletter host requires for SMTP authentication.</div>


<h2 id="newsletter_smtp_email_account_password">Newsletter SMTP Email Account Password</h2>

<div class='indent'>Key: <b>NEWSLETTER_EMAIL_SMTPAUTH_PASSWORD</b><br />
Path: <b>Configuration > Email</b><br />
Description: Enter the password for your newsletter SMTP mailbox.</div>


<h2 id="newsletter_smtp_email_mail_host">Newsletter SMTP Email Mail Host</h2>

<div class='indent'>Key: <b>NEWSLETTER_EMAIL_SMTPAUTH_MAIL_SERVER</b><br />
Path: <b>Configuration > Email</b><br />
Description: Enter the DNS name of your Newsletter SMTP mail server if you are using a separate email server for bulk email.</div>


<h2 id="newsletter_smtp_email_mail_server_port">Newsletter SMTP Email Mail Server Port</h2>

<div class='indent'>Key: <b>NEWSLETTER_EMAIL_SMTPAUTH_MAIL_SERVER_PORT</b><br />
Path: <b>Configuration > Email</b><br />
Description: Enter the IP port number that your newsletter SMTP mailserver operates on.<br><br>Default: 587<br>Typical values are:<br>587 - encrypted SMTP<br>465 - older MS SMTP port</div>


<h2 id="newsletter_modules">Newsletter Modules</h2>

<div class='indent'>Key: <b>NEWSLETTER_MODULES</b><br />
Path: <b>Configuration > Email</b><br />
Description: Enter a comma-separated list of the modules that should use the newsletter settings when sending email (rather than the regular email settings).</div>


