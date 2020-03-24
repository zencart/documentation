---
title: Shipping Modules - Miscellaneous Questions
description: Zen Cart Shipping Modules - Miscellaneous Questions
category: shipping
weight: 5
---

### Can I skip the shipping selection page when shipping is free?
Set all products as free shipping in by editing each one and setting the button in the middle of the product-info/edit screen.

Then enable the free shipping module..

This will allow shipping to totally bypass the shipping page.

<hr />

### How do I enable free shipping for orders more than $XX?
Open your Admin, point your cursor at Modules on the top menu, choose Order Total from the dropdown. Then select Shipping from the list. If the module is not installed click the install. After it is installed click edit and configure to allow free shipping.

<hr />

### How do you clone a shipping module? 
See [this FAQ](/dev/code/modules/clone_shipping/) in the development area.

<hr />

### How can I set up individual shipping charges per item? 
The per-weight shipping module can be used for this.

1. Turn on the Per-Unit (perweightunit) shipping module in Admin->Modules->Shipping

2. Now manually edit *each* product and enter the shipping cost as the product "weight".
    This module uses the product-weight as the shipping rate for this product ... ie: it is no longer the weight -- it is only the shipping cost.

3. Turn off weight display everywhere, since it is no longer meaningful.

    a) Admin->Catalog->Product Types->[select your product type]->Edit Layout->Show weight->false

    b) Admin->Configuration->Shipping/Packaging->Display Number of Boxes and Weight Status

    c) Admin->Configuration->index listing / all listing / new listing / featured listing ... turn off the weight on these

<hr />
