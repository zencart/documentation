---
title: Site Specific Overrides 
description: More ways to customize your cart's behavior without modifying core files
category: customizing
weight: 10
---

Starting in Zen Cart 1.5.8, a file called `includes/extra_datafiles/dist-site_specific_overrides.php` is provided.  

Copy this file to 

`includes/extra_datafiles/site_specific_overrides.php`

and customize to taste. 

The following behaviors can be enabled or disabled by this file: 

- displaying the [Brands page](/user/storefront_pages/brands/) link in the Information sidebox 
- displaying the About Us link in the Information sidebox

Example: turn on the Brands page link in the Information sidebox:

```
$flag_show_brand_sidebox_link = true;
```

Information on the [admin site-specific overrides file](/user/admin/site_specific_overrides/) is also available. 
