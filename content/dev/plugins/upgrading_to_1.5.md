---
title: Upgrading 1.3.X era plugins 
description: Upgrading old Zen Cart plugins for 1.5 Compatibility
category: plugins
weight: 1
---


A number of features have been changed or added in v1.5.0. This may have broken some addons which were built for older versions. The following information may be helpful as you prepare to upgrade your site and/or convert your custom code or addons to work with v1.5.

## Admin Menu Controls

The `admin/includes/boxes/xxxxxx_dhtml.php` files and `admin/includes/boxes/extra_boxes/*.php` files which formerly controlled menu choices have been removed. These files no longer have any effect on admin menus.
Instead you will need to use the Admin Profiles menu to grant permissions to user profiles and profiles to users.
You can use the admin menus (Admin Page Registration) to add the appropriate menu choices as well.

Plugin authors can use function calls to `zen_register_admin_page()` and `zen_deregister_admin_pages()` to install/remove menu options for their plugins.

## Rewriting addon admin pages to use form POSTs instead of GETs

In the interest of mitigating against CSRF issues, it is necessary to use GET parameters *only* when indicating selection criteria, and NEVER when performing destructive actions or database write operations.
There is a forum thread which outlines some guidance in the process of rewriting addons in this way: https://www.zen-cart.com/showthread.php?t=184616

Forms in v1.5.0 and newer must use security tokens such as those set by properly using `zen_draw_form` instead of hard-coded
tags and must use POSTs for all CRUD actions, leaving GETs for only filter-related activities.

## Moving to the Encapsulated Plugin manager 

As an recommended next step, follow the guide [Converting an older plugin](/dev/plugins/encapsulated_plugins/converting/) to use the new encapsulated plugin manager.  

## Upgrading for PHP8+/Zen Cart 1.5.8+

Please see [Upgrading plugins to work with PHP8+/1.5.8+](https://docs.zen-cart.com/dev/plugins/upgrading_to_158/).


