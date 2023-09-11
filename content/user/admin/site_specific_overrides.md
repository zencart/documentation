---
title: Admin Site Specific Overrides 
description: How to customize your admin behavior without modifying core files
category: admin 
weight: 10
---

## Admin Setting Overrides 

Starting from Zen Cart 1.5.8, a file called `admin/includes/extra_datafiles/dist-site_specific_admin_overrides.php`  
is now used to control multiple minor admin options.

Copy this file to 

`admin/includes/extra_datafiles/site_specific_admin_overrides.php`

and customize to taste. 

Many behaviors can be enabled or disabled by this file, such as:
- indicating whether the downloads manager page should show the file date
- modifying the [order display](/user/admin_pages/customers/order_display_options/) for images, tax display, etc. 
- showing product images/attribute images on the packing slip/invoice 
- show attribute data in the Dashboard Orders popup
- number of rows to display in the Dashboard Orders
- show Quick View popup on the Orders listing
- show attribute data in the Quick View popup on the Orders listing
- show the Zone column in the Orders listing
- show the customer registration IP column in the Customers listing
- (developers) whether to enable debug on the `zcDate` class.
- (developers) whether to load the [Font Awesome](/user/template/font_awesome/) v4 shim for backwards compatibility.

See the file itself for specifics and details.

Information on the [storefront site-specific overrides file](/user/customizing/site_specific_overrides/) is also available. 

## Admin CSS Overrides 

Starting in Zen Cart 1.5.8a, a file called `admin/includes/css/dist-site-specific-styles.php` is provided.  

Copy this file to 

`admin/includes/css/site-specific-styles.php`

and customize to taste. 

