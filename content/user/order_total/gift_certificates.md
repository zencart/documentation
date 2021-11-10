---
title: Gift Certificates
description: Store vouchers 
category: order_total
weight: 10
---

To sell Gift Certificates in your store, you need to create them as products, according to the specifications below. 

Gift Certificates may be optionally queued for release by the administrator so that they are not available immediately after purchase. (Some storeowners prefer to do this for extra security.) 

If the *Queue Purchases* setting in Admin > Modules > Order Total > Gift Certificates is used, then after purchase, the administrator must "release" the gift certificate. A button indicating queued gift certificates is shown in the admin panel.  Once the release is done, the Gift Certificate funds are made available to the customer, by adding them to the Customer's Gift Certificate balance.  

If the *Queue Purchases* setting is not used, the funds are made available in the Customer's Gift Certificate balance immediately after purchase.  

The customer can then USE those funds for themselves, OR they can email them to friend(s) via the links provided automatically in the store (esp shopping cart sidebox). They can email as much as they want, to various people, up to the amount they've purchased. Whoever they email it to will receive a new redemption code and can follow the redemption process, either redeeming via the email link, going to the Gift Certificate FAQ page or redeeming during checkout. The customer can email the funds again if they wish or use the GV Balance for themselves.  

Gift Certificates show up at checkout on the Payment page: 

![Gift Certificates at Checkout](/images/gift_certificates.png) 

And on the My Account page: 

![Gift Certificates on My Account](/images/my_account_gift_certificates.png) 

Your customers can also redeem gift certificates on the GV FAQ page (`index.php?main_page=gv_faq`).


### How do I create a Gift Certificate? 

1\. In the Admin, make a new category called Gift Certificates. Add a product to the category called Gift Certificates.  

2\. On the Product Information Page, use these settings: 

*   Products Name: Gift Certificate
*   Product Priced by Attributes: This is up to you, if you choose to price by attributes you only need a single 'product'.  Otherwise you need gift certificates at various price points. 
*   Tax Class: choose appropriate
*   Products Price (Net): Your price or zero if pricing by attributes.
*   Products Price (Gross): figured automatically
*   Product is Virtual: Yes, Skip Shipping
*   Always Free Shipping: No.
*   Products Description: Your description.
*   Products Quantity: leave blank or put in a large number to track number sold.  
    If you are finding that you cannot add a Gift Certificate to your cart while shopping, try adding a quantity here!
*   Products Model: GIFT-xxxxx (Note: The model MUST begin with the string "GIFT")

3\. Click Preview and then Save it.  

4\. Now go to Modules > Order Total, select Gift Certificates, and click Install. This installs the Gift Certificate module. 

### How do I sell Gift Certificates?
1\. Create Gift Certificate products as described above  
2\. Enable the Gift Certificate order-total module, as described above  
3\. Draw attention to gift certificates on your store, perhaps by creating a home-page graphic with a link to your gift-certificates category.  Sometimes people will create a new sidebox just for drawing attention to this sort of thing.  
4\. When Gift Certificates are purchased, be sure to log into your Admin area and release them if you've configured it to queue them rather than auto-release them.

### Can a customer use multiple gift certificates at a time?
A customer can enter as many Gift Certificates as they want on the checkout_payment page or gift-certificate redemption page (`index.php?main_page=gv_faq`), and then apply what ever portion of their Gift Certificate Balance to the order.

**NOTE:** Gift Certificates can also be claimed by using the link provided in the email and logging in to claim the Gift Certificate to add it to their available balance.   And then they are free to apply the amount to use against any future order during checkout on the checkout_payment.

**NOTE:** Gift Certificates are sometimes also called "Gift Vouchers" by our friends in the United Kingdom.  You will hear these terms used interchangeably. 

### What admin pages show Gift Certificate activity? 

The Zen Cart admin has the following pages related to Gift Certificates: 

- [Admin > Discounts > Gift Certificate Queue](/user/admin_pages/discounts/gift_certificate_queue/)
- [Admin > Discounts > Gift Certificates Sent](/user/admin_pages/discounts/gift_certificates_sent/)
- [Admin > Discounts > Send Gift Certificate](/user/admin_pages/discounts/send_gift_certificate/)

If you don't see these pages, it's because you haven't yet installed gift certificates. Go to Admin > Modules > Order Total, select Gift Certificates, and press Install. 
