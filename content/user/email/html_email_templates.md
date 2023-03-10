---
title: HTML Email Templates
description: How HTML mail is formatted in Zen Cart 
category: email
weight: 10
---

### Email System Settings relating to rich text messages:

In Admin >Configuration > Email 

a. Make sure your "**E-Mail Transport Method**" is set appropriately for the webserver you're using. Using SMTPAUTH is strongly advised. Do not use "PHP" unless nothing else works.  

b. **Enable HTML Emails?** = "true" [^1]

c. **Send E-Mails** = true  

d. **Email Archiving Active?** = If you are testing or debugging, we recommend setting this to "true" -- note, this will increase your database size regularly.  [^2] 

[^1]: Prior to Zen Cart 1.5.5, this option was called **Use MIME HTML When Sending Emails**. 

[^2]: To access the email archive, see [Email Archive Manager](/user/email/email_archive_manager/). 

### What if I have my own HTML code to paste into an email? (rather than using an editor in my browser)

You can optionally toggle the HTML editor's "source" option on (check the box, or click the symbol), and just paste raw HTML into the editor directly, if you wish.  

Further, if you leave the editor disabled, but enable sending HTML messages, you can simply paste the raw HTML in the rich text field directly.  

### What about text-only messages/customers?

You can enter customizable TEXT-ONLY content in the lower section, which will be sent along with the HTML in case readers don't have HTML-compatible email clients. If you leave the "TEXT ONLY" area blank, your HTML content will be converted (roughly by removing HTML tags) and sent along as the Text portion anyway.

## HOW TO USE the HTML Mail Template System

The email template system operates through the 
`email_*.htm` files in your `/email` folder.

## Template Search Order
The HTML template which will be used when `zen_mail` is called is determined according to the following order of search, checking in the `email/` folder at the top of your cart installation.  The first match causes the check to stop, and that template is used. 

In each check below, the file prefix `email_template_` and suffix `.html` is added when looking for a file.  Remove `_extra` or `_admin` from `$module`. 

- look for a file named `email_template_$module.html` under the language folder 
- look for a file named `email_template_$module.html` under the main folder
- look for a file named `email_template_$current_page_base.html` under the language folder 
- look for a file named `email_template_$current_page_base.html` under the main folder
- look for a file named `$block['EMAIL_TEMPLATE_FILENAME']`
- look for a file named `default` under the language folder  
- look for a file named `default` under the main folder  

Consider the following scenario: 
- `$current_page_base` = `send_po` 
- `$module` = `vendor_extra`
- `$block['EMAIL_TEMPLATE_FILENAME']` = `email/email_template_bigcorp`
- Language being used is English 

The search goes as follows.  As soon as a matching file is found, the search stops, and that template is used. 

```
email/en/email_template_vendor.html 
email/email_template_vendor.html 
email/en/email_template_send_po.html 
email/email_template_send_po.html 
email/email_template_bigcorp.html
email/en/email_template_default.html 
email/email_template_default.html 
```


## MULTIPLE LANGUAGES

You can duplicate the template files into language-specific folders using the language "short" code, using the following format:  

- `/email/` = this is your English/master set of files  
- `/email/en/` = English (if English is not the default language) 
- `/email/fr/` = French  
- `/email/de/` = German  
- `/email/es/` = Spanish  
...  

If you don't copy a certain file into the language folder, the master will be used.  

## EMAIL TEMPLATE STYLESHEET

Since HTML-based email standards are varied more widely than the shape of each cloud in the sky, it's impossible to predict the behaviour of any email client's output rendering. **Thus, linked stylesheets are not recommended.** Some email reader/clients will completely reject an email that has a stylesheet link ref in it.

In coding your HTML email message templates, <u>**it's best to code to HTML 3.2 and CSS1 standards**</u> for optimum compatibility.

# TEMPLATE SYSTEM KEYWORDS MATRIX

The following key words are replaced with active HTML by the various modules. Simply retain them in any revisions you make to your template structure, and all should come out just fine !!!  
Note that all template tags should be prefixed with a $  

### All Modules
```
$EMAIL_FIRST_NAME (most modules supply the customer names)  
$EMAIL_LAST_NAME  

$EMAIL_TO_NAME  
$EMAIL_TO_ADDRESS (TO: email address)  
$EMAIL_FROM_NAME  
$EMAIL_FROM_ADDRESS (FROM: email address.... default is EMAIL_FROM defined in Admin)  
$EMAIL_STORE_NAME (Defined in Admin | My Store)  
$EMAIL_STORE_OWNER (Store Owner's NAME -- defined in Admin)  
$EMAIL_STORE_URL (Preformatted A HREF for your store's URL, using STORE_NAME for the displayed text)  
$EMAIL_DATE_LONG (ie: Monday June 14, 2004 11:28 am)  
$EMAIL_DATE_SHORT (ie: 06/14/2004)  
$BASE_HREF (store http root)  
$EXTRA_INFO (this is the "office-use-only" section at the bottom of messages cc'd to Admin)  
```

These values are defined in `includes/languages/YOURLANGUAGE/email_extras.php`:  

```
$EMAIL_DISCLAIMER (general disclaimer)  
$EMAIL_SPAM_DISCLAIMER (disclaimer re: SPAM -- should be customized to your country's laws...and of course you should abide by them!)  
$EMAIL_FOOTER_COPYRIGHT  
$EMAIL_MESSAGE_HTML (this is any composed text (via editors) that you plan to send)  
```

## ADMIN AREA:

### Coupon
```
Dear $EMAIL_FIRST_NAME $EMAIL_LAST_NAME,  
$EMAIL_MESSAGE_HTML (message composed in Admin)  
$COUPON_TEXT_TO_REDEEM ("You've received a coupon")  
$COUPON_TEXT_VOUCHER_IS (The voucher number is:")  
$COUPON_CODE (Actual voucher number)  
$COUPON_DESCRIPTION (Coupon description, if supplied in Admin area when coupon was created)  
$COUPON_TEXT_REMEMBER ("Keep this number safe so you don't forget it")  
$COUPON_REDEEM_STORENAME_URL ("To redeem, come visit us at our store: +URL")  
```

### GV-Mail-From-Admin
```
Dear $EMAIL_FIRST_NAME $EMAIL_LAST_NAME  
$EMAIL_MESSAGE_HTML (Message composed in Admin)  
$GV_WORTH ("You've received a GV worth: " )  
$GV_AMOUNT (GV amount)  
$GV_REDEEM (To redeem, goto our store, or click here:)  
$GV_CODE_URL (URL to redeem GV)  
```

### GV-Queue in Admin (to release purchased GV's after screening)
```
Dear $EMAIL_FIRST_NAME $EMAIL_LAST_NAME  
$GV_NOTICE_INTRO (You purchased a GV from our store: URL) (optional)  
$GV_NOTICE_AMOUNT_URL (You purchased a GV of $$$$ from our store: URL)  
$GV_NOTICE_VALUE (Amount of GV purchased, and now being released)  
$TEXT_REDEEM_COUPON_MESSAGE_BODY (null unless defined in lang file)  
$TEXT_REDEEM_COUPON_MESSAGE_FOOTER (null unless defined in lang file)   
```

### Low Stock
```
- $EMAIL_SUBJECT  
- $EMAIL_MESSAGE_HTML -- contains the low-stock details generated by the checkout process  
```

### Newsletters & Product Notifications, and Admin Emails
```
Dear $EMAIL_FIRST_NAME $EMAIL_LAST_NAME,  
$EMAIL_MESSAGE_HTML (composed by Admin)  
```

### Order Status Updates from Admin
```
$EMAIL_CUSTOMERS_NAME (extracted from Orders table -- combines first/last names based on what's in DB)  
$EMAIL_STORE_NAME  
$EMAIL_TEXT_ORDER_NUMBER (Order Number from database)  
$EMAIL_TEXT_INVOICE_URL (URL to access "My Account History")  
$EMAIL_TEXT_DATE_ORDERED (Order Date)  
$EMAIL_TEXT_STATUS_UPDATED ("Has been updated to:")  
$EMAIL_TEXT_STATUS_LABEL ("New Status:")  
$EMAIL_TEXT_NEW_STATUS (actual status description and comments)  
$EMAIL_TEXT_STATUS_PLEASE_REPLY ("Please reply to this address if you have questions")  
```

### Password Forgotten:
```
$EMAIL_SUBJECT ("password reset requested")  
$CUSTOMERS_NAME (Admin or customer's name)  
$EMAIL_MESSAGE_HTML (actual pwd reset info)  
```

## CATALOG AREA:

### Contact-Us
NOTE: Contact-Us emails are always sent as text. This helps prevent some spam issues.


### Welcome Email
```
$EMAIL_GREETING (Mr/Ms/Dear + first and/or last-names)  
$EMAIL_WELCOME ("Welcome to ....storename....")  

$COUPON_BLOCK ... this already CONTAINS the following, and is only displayed IF they have been set for new customers via the Admin | My Store | GV/Coupons.  
.....$COUPON_TEXT_VOUCHER_IS  
.....$COUPON_DESCRIPTION  
.....$COUPON_TEXT_TO_REDEEM  
.....$COUPON_CODE  
$GV_BLOCK ... this already contains the following, and is only displayed if GV's have been set for new customers, see coupons above.  
.....$GV_WORTH  
.....$GV_REDEEM  
.....$GV_CODE_URL  

$EMAIL_MESSAGE_HTML (the actual welcome message: defined by the "EMAIL_TEXT" constant)  
$EMAIL_CONTACT_OWNER  
$EMAIL_CLOSURE  
```

### GV Send to a friend, after purchased and applied to my account

GV Pic is displayed, with these beside it:   
```
......$EMAIL_GV_AMOUNT   
......$GV_REDEEM_CODE  
$EMAIL_STORE_NAME  
$EMAIL_GV_TEXT_HEADER (I'm sending you a GV)  
$EMAIL_GV_AMOUNT (Amount of)  
$EMAIL_GV_FROM (From my name)  
$EMAIL_GV_MESSAGE ("With a message from me")  
$EMAIL_GV_SEND_TO (Your name)  
$EMAIL_MESSAGE_HTML (My message -- entered before sending)  
$GV_REDEEM_HOW (How to redeem the GV)  
$GV_REDEEM_URL (URL to redeem)  
$EMAIL_GV_FIXED_FOOTER (If you're having problems redeeming, enter it during checkout, or contact storeowner)  
$EMAIL_GV_SHOP_FOOTER (null at present)  
```

### Order-Confirmation
```
$EMAIL_TEXT_HEADER ("Order Confirmation")  
$INTRO_STORE_NAME  
$INTRO_ORDER_NUM_TITLE ("Order Number:")  
$INTRO_ORDER_NUMBER (actual order number)  
$INTRO_DATE_TITLE ("Ordered on:")  
$INTRO_DATE_ORDERED (Date ordered)  
$INTRO_URL_TITLE (Description in A HREF to My Account)  
$INTRO_URL_VALUE (A HREF to My Account)  
$ORDER_COMMENTS (Customer's comments entered at order time)  
$PRODUCTS_TITLE ("Product Details:")  
$PRODUCTS_LIST (Detailed list of products and attributes and prices)  
$ORDER_TOTALS (Order totals)  
$HEADING_ADDRESS_INFORMATION ("Address Info:")  
$ADDRESS_DELIVERY_TITLE ("Delivery address:")  
$ADDRESS_DELIVERY_ADDRESS (Actual delivery address on order)  
$SHIPPING_METHOD_TEXT ("Shipping Method")  
$SHIPPING_METHOD_TITLE (Shipping method selected)  
$ADDRESS_BILLING_TITLE ("Billing address:")  
$ADDRESS_BILLING_DETAIL (Billing address on order)  
$PAYMENT_METHOD_TEXT ("Payment Method:")  
$PAYMENT_METHOD_TITLE (Payment method selected)  
$PAYMENT_METHOD_FOOTER (Payment method footer, if any)
```
