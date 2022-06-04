---
title: Admin Site Specific Overrides 
description: How to customize your admin behavior without modifying core files
category: admin 
weight: 10
---

Starting in Zen Cart 1.5.8, a file called `admin/includes/extra_datafiles/dist-site_specific_admin_overrides.php` is provided.  

Copy this file to 

`admin/includes/extra_datafiles/site_specific_admin_overrides.php`

and customize to taste. 

The following behaviors can be enabled or disabled by this file: 
- Enable/disable zcDate debug
- The [order display](/user/admin_pages/customers/order_display_options/) for images, tax display, etc. 


Example: disable product images on packing slip and invoice: 
```
$show_product_images = false;
```

Example: disable product images on invoice only: 
```
if ($_GET['cmd'] == 'invoice') { 
   $show_product_images = false;
}
```

Information on the [storefront site-specific overrides file](/user/customizing/site_specific_overrides/) is also available. 
