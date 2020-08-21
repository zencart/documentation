---
title: Product Types > Layout Settings
description: Zen Cart Product Types > Layout Settings Admin Page 
category: admin_pages
weight: 21
---

Each [product type](/user/admin_pages/catalog/product_types/) can choose to show or hide specific fields. 

The Product Types Layout Settings page has a series of flags that allow you to enable or disable the fields that are shown on the Product Info page *for the currently selected product type*.   These augment the product-type-independent fields which are set on Admin > Configuration > Layout Settings. 

![Layout Settings page](/images/layout_settings.png)

For example: 

- To turn off the display of Model number, click `Show Model Number`, click the dropdown and select `False`, and then press `Update`.

### Issue: I am turning off the display of fields in Layout Settings, but they are still displayed on my product info page. 

This can occur when template authors choose not to respect the flags that Zen Cart uses.  To fix this, edit `includes/templates/YOURTEMPLATE/templates/tpl_product_info_display.php` and modify the code that handles the display of the field you wish to turn off. 

If you are a developer, see [technical information on product types](/dev/code/product_types/). 
