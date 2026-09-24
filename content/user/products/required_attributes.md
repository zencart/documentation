---
title: Required Attributes not working 
description: I want to force a decision - how do I do this? 
category: products
weight: 10
---

Problem: When I add a required attribute to an item, such as a color that must be specified, and I enable the Required button on the attribute, it is still letting customers add the item to the cart without the attribute being set.

Explanation: "Required" is only for "text" input fields. (Hence the description of "Text Required").  However, you can still set a default value for a dropdown or radio button attribute using one of the techniques described below. 

To force selection of an attribute, there are two options: 

1. Create a "Please Select" option (for dropdowns) 

    a. add an attribute that is Display-Only (ie: a color swatch that says "Please Select a Color").

    b. make it the default.
This forces the customer to choose something "other than" the default (since the "default" is set to "display only").

2. Set a default value (for radio buttons) 

    a. Go to the [Attributes Controller](/user/admin_pages/catalog/attributes_controller/) and select the product in question (you will need to select the category, then the product, then press *Display*).  The attributes will be shown below the product. 

    b. Pick the attribute you want to be the default, and press the Edit button on the right side of that attribute.

    c. Set the *Default Attribute to be Marked Selected:* radio button to *Yes*.

    d. Press the *Update* button to save this change. 

**Please Note:** This behavior works properly in the latest version of Zen Cart; older versions may still show an unselected radio button.  Be sure to test this carefully; you may need to upgrade if you have an older version and it does not work. 

