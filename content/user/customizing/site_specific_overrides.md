---
title: Site Specific Overrides 
description: More ways to customize your cart's behavior without modifying core files
category: customizing
weight: 10
---

## Setting Overrides 

Starting in Zen Cart 1.5.8, a file called `includes/extra_datafiles/dist-site_specific_overrides.php` is provided.  

Copy this file to 

`includes/extra_datafiles/site_specific_overrides.php`

and customize to taste. 

Many behaviors can be enabled or disabled by this file, such as:

- displaying the About Us link in the Information sidebox
- displaying the [Brands page](/user/storefront_pages/brands/) link in the Information sidebox 
- (developers) whether to enable debug on the `zcDate` class
- (developers) whether to bypass loading string-matches of legacy language files (see [Substring Matching](/dev/code/158_order_language_files/) for details).
- (developers) whether to disable loading the [Font Awesome](/user/template/font_awesome/) v4 shim if backwards compatibility is not needed.

See the file itself for specifics and details.

Information on the [admin site-specific overrides file](/user/admin/site_specific_overrides/) is also available. 

## Non-Database Setting Overrides 

Starting in Zen Cart 1.5.8, a file called `/includes/init_includes/dist-init_site_specific_non_db_settings.php` is provided.  

Copy this file to 

`/includes/init_includes/init_site_specific_non_db_settings.php`

and customize to taste. The settings that may be altered in this file are  listed in the file `includes/init_includes/init_non_db_settings.php`.

