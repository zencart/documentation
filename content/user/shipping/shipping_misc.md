---
title: Shipping Modules - Miscellaneous Questions
category: shipping
weight: 5
---

{{< misc >}} 

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
### How do I clone a shipping module? 
See [the clone shipping module FAQ](/dev/code/modules/clone_shipping/) in the development area.

---
<!-- please keep this at the end --> 
{{< faq_questions >}}
