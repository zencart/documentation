---
title: Gift Certificates
description: Zen Cart Gift Certificates
category: order_total
weight: 10
---

To sell Gift Certificates in your store, you need to create them as specific products (according to special requirements, outlined below):  

1\. In the Admin, make a new category called Gift Certificates. Add a product to the category called Gift Certificates.  
2\. On the Product Information Page fill in the blanks as follows:  

*   Products Status: In Stock
*   Date Available: leave blank
*   Products Manufacturer: leave blank
*   Products Name: Gift Certificate
*   Product is Free: No
*   Product is Call for Price: No
*   Product Priced by Attributes: Yes No  
    This is up to you, if you choose to price by attributes you only need a single 'product'.
*   Tax Class: choose appropriate
*   Products Price (Net): Your price or zero if pricing by attributes.
*   Products Price (Gross): figured automatically
*   Virtual Products do not have a shipping charge and do not require a shipping address such a Services, Gift Certificates, etc. Always Free Shipping does not have a shipping charge, but do require a shipping address Downloads are assumed to be Virtual Products - Neither option needs to be marked
*   Product is Virtual: Yes, Skip Shipping
*   Always Free Shipping: No.
*   Products Quantity Box Shows: Yes, Show
*   Product Qty Minimum: leave blank
*   Product Qty Maximum: 0 = Unlimited, 1 = No Qty Boxes or Max ##
*   Product Qty Units: leave blank
*   Product Qty Min/Unit Mix: leave blank
*   Products Description: Your description.
*   Products Quantity: leave blank or put in a large number to track number sold.  
    If you are finding that you cannot add a Gift Certificate to your cart while shopping, try adding a quantity here!
*   Products Model: GIFT-xxxxx
*   The model MUST begin with GIFT
*   Products Image: Upload an image
*   Upload to directory: choose directory
*   Products URL: leave blank
*   Products Weight: leave blank

3\. Click Preview and then Save it.  
4\. Now go to Modules > Order Total, select Gift Certificates, and click Install. This installs the Gift Certificate module. 

### HOW DOES IT WORK THEN ?

Gift Certificates may be optionally queued for release by the administrator. 

If the *Queue Purchases* setting in Admin > Modules > Order Total > Gift Certificates is used, then after purchase, the administrator must "release" the gift certificate. A button indicating queued gift certificates is shown in the admin panel.  Once the release is done, the Gift Certificate funds are made available to the customer, by adding them to the Customer's Gift Certificate balance.  

If the *Queue Purchases* setting is not used, the funds are made available in the Customer's Gift Certificate balance immediately after purchase.  

The customer can then USE those funds for themselves, OR they can email them to friend(s) via the links provided automatically in the store (esp shopping cart sidebox). They can email as much as they want, to various people, up to the amount they've purchased. Whoever they email it to will receive a new redemption code and can follow the redemption process, either redeeming via the email link, going to the Gift Certificate FAQ page or redeeming during checkout. The customer can email the funds again if they wish or use the GV Balance for themselves.  

### How do I sell Gift Certificates?
1\. Create Gift Certificate products as described above  
2\. Enable the Gift Certificate order-total module, as described above  
3\. Draw attention to gift certificates on your store, perhaps by creating a home-page graphic with a link to your gift-certificates category.  Sometimes people will create a new sidebox just for drawing attention to this sort of thing.  
4\. When Gift Certificates are purchased, be sure to log into your Admin area and release them if you've configured it to queue them rather than auto-release them.

### Can a customer use multiple gift certificates at a time?
A customer can enter as many Gift Certificates as they want on the checkout_payment page or gift-certificate redemption page, and then apply what ever portion of their Gift Certificate Balance to the order.

**NOTE:** Gift Certificates can also be claimed by using the link provided in the email and logging in to claim the Gift Certificate to add it to their available balance.   And then they are free to apply the amount to use against any future order during checkout on the checkout_payment.

**NOTE:** Gift Certificates are sometimes also called "Gift Vouchers" by our friends in the United Kingdom.  You will hear these terms used interchangeably. 

