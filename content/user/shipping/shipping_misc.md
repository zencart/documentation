---
title: Shipping Modules - Miscellaneous Questions
category: shipping
weight: 5
---

{{< misc >}} 

--- 
### Can I skip the shipping selection page when shipping is free?
Set all products as free shipping in by editing each one and setting the button in the middle of the product-info/edit screen.

Then enable the free shipping module..

This will allow shipping to totally bypass the shipping page.

--- 

### How do I enable free shipping for orders more than $XX?
Go to [Admin > Modules > Order Total](/user/admin_pages/modules/order_total/).
Then select *Shipping* from the list. If the module is not installed click the install. After it is installed click edit and configure to allow free shipping.

---
### How do you clone a shipping module? 
See [the clone shipping module FAQ](/dev/code/modules/clone_shipping/) in the development area.

--- 

### How can I set up individual shipping charges per item? 
The per-weight shipping module can be used for this.

1. Turn on the Per-Unit (perweightunit) shipping module in [Admin > Modules > Shipping](/user/admin_pages/modules/shipping/)

2. Now manually edit *each* product and enter the shipping cost as the product "weight".
    This module uses the product-weight as the shipping rate for this product.  This means the `weight` field is no longer the weight -- it is only the shipping cost.

3. Turn off weight display everywhere, since it is no longer meaningful.

    a) [Turn off weight display on the product info page](/user/template/basic_customizations/#can-i-turn-off-fields-from-my-product-info-page). 

    b) Admin > Configuration > Shipping/Packaging > Display Number of Boxes and Weight Status

    c) Admin > Configuration > Index Listing / All Listing / New Listing / Featured Listing - all must be changed to not display the weight. 

---
<!-- please keep this at the end --> 
{{< faq_questions >}}
