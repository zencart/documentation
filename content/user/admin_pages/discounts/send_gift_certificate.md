---
title: Send a Gift Certificate 
category: admin_pages
weight: 30 
---

If you haven't read [about Gift Certificates](/user/order_total/gift_certificates/) yet, please start there. 

The Discounts > Send a Gift Certificate page allows you to generate gift certificates and issue them by email.

## To generate/mail a gift certificate from your web site
Mailing gift certificates requires the Gift Certificates module to be installed (under Admin > Modules > Order Total). 

**Note:** Gift Certificates are recognized by redemption code, and not a name. 

1. Log in to the Zen Cart Admin section.


2. Go to Discounts > Send a Gift Certificate.


3. In the drop down menu select and existing customer to send the gift certificate, or enter a new address in the field below it.


4. Make sure that the default from address is who you want the email to be from.


5. Enter email subject like, 'You have a Gift Certificate from a web site running Zen Cart.'


6. Enter the amount value of the gift certificate.


7. Enter a message to go with it.


8. Click send mail.


9. On the next page review and send the certificate.


Your customer will receive an email that look something like this.

```
BODY TEXT THAT YOU ENTERED

The Gift Certificate is worth $20.00

To redeem this Gift Certificate, please click on the link below. Please also write down the Redemption Code which is 20b171589e in case you have any problems.

http://www.YOURSITE.com/store/index.php/gv_redeem/gv_no/20b171589e

or visit http://www.YOURSITE.com/store/ and enter the code during the checkout process


This email address was given to us by you or by one of our customers. If you feel that you have received this email in error, please send an email to YOURSITE@YOURMAIL.com
```

Then, when they go to checkout, payment (either in part or in full) by gift certficate will be permitted.  

![Gift Certificates at Checkout](/images/gift_certificates.png)

In the case shown, for example, they could pay up to $50 of the amount due with their gift certificate balance.

## Releasing Gift Certificates Created by Admin 
For stores that use the *Queue Purchases* setting in Admin > Modules > Order Total > Gift Certificates, purchased Gift Certificates must be released before they can be used. 

Gift Certificates created by the admin are not subject to this restriction; no release is required. 

