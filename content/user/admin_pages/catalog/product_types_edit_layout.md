---
title: Product Types->Layout Settings
description: Zen Cart Product Types->Layout Settings Admin Page 
category: admin_pages
weight: 21
---

This page has a series of flags that allow you to enable or disable the fields that are shown on the Product Info page.  

For example: 

- To turn off the display of Model number, click `Show Model Number`, click the dropdown and select `False`, and then press `Update`.

### Issue: I am turning off the display of fields in Layout Settings, but they are still displayed on my product info page. 

This can occur when template authors choose not to respect the flags that Zen Cart uses.  To fix this, edit `includes/templates/YOURTEMPLATE/templates/tpl_product_info_display.php` and modify the code that handles the display of the field you wish to turn off. 

