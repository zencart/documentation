---
title: Attributes - How do I make dropdowns start with "Please Select" 
description: Prompting the customer to select an option value 
category: products
weight: 10
---

In a dropdown, you can start with an attribute value:

![Dropdown - no default](/images/dropdown_no_default.png)

or you can start with a prompt like "Please Choose" or "Select a Value": 

![Dropdown - default](/images/dropdown_default.png)

The former requires no special steps; just add options to products as described in [Attributes - adding to products](/user/products/attributes/). 

The latter requires setting a [default option value](/user/products/attributes/#default-option-value) for each Option Name that will have this behavior. 

- Go to Admin > Catalog > Option Value Manager 
- Select the Option Name that will have this option value.  In the second image, it would be "Size." 
- Create an value option value with the prompt you wish to use (e.g. "Please Select"). 
- Go to Attributes Controller, and select the product you want to operate on.
- Select the option name (e.g. "Size") and option value (e.g. "Please Select").
- Click "Used For Display Purposes Only" = "Yes.
- Click "Default Attribute to be Marked Selected" = "Yes.
- Click the Insert button. 

**Note:** To make this option show at the top of the list, give it a sort order less than all the other sort orders when adding it in Attributes Controller.  You may use a negative number if needed. 

