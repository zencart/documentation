---
title: Required Attributes not working 
description: I want to force a decision - how do I do this? 
category: products
weight: 10
---

Problem: When i set a attribute to an item like a color that must be specified and I enable the Required button on the attribute it is letting customers add items to the cart without giving a required attribute.

"Required" is only for "text" input fields. (Hence the description of "Text Required").  However, you can still set a default value for an attribute using one of the techniques described below. 

To force selection of an attribute, there are two options: 

1. Create a "Please Select" option (for dropdowns) 

    a. add an attribute that is Display-Only (ie: a color swatch that says "Please Select a Color").

    b. make it the default.
This forces the customer to choose something "other than" the default (since the "default" is set to "display only").

    **NOTE:** This doesn't work for checkboxes.

2. Set a default value (for radio buttons) 

    a. Go to the [Attributes Controller](/user/admin_pages/catalog/attributes_controller/) and select the product in question (you will need to select the category, then the product, then press *Display*).  The attributes will be shown below the product. 

    b. Pick the attribute you want to be the default, and press the Edit button on the right side of that attribute.

    c. Set the *Default Attribute to be Marked Selected:* radio button to *Yes*.

    d. Press the *Update* button to save this change. 
 
