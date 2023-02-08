---
title: Admin Templating Capability
description: How to Customize Admin Pages Without Touching Core Files
weight: 10
---


In Zen Cart v1.x the Admin section is driven by pages that combine a lot of business logic with presentation logic. 
That is, there isn't much of a "template" system, especially when compared to the Storefront side of the application.

While it embraces an MVC structure, it doesn't currently fully separate presentation from backend logic.

That said, since v1.5.7 many (v1.5.8 expands it to _all_) admin pages support some degree of per-page CSS and JS file inclusion. 
(This is driven by the use of `admin_html_head.php` instead of directly outputting all the `<head>` tag content directly within the page itself.)

In the examples below, `PAGENAME` and `pagename` refer to either the `cmd=pagename` value or the `/admin/pagename.php` value, depending on the page/URL.


## Per-Page CSS Files

You may put your custom CSS for individual Admin pages into page-specific files that will automatically load on those pages.

The convention (and loading order) is:

- `/YOURADMIN/includes/css/stylesheet.css` (this is a core file, but is loaded on every page; only edit if your changes are for everywhere)
- `/YOURADMIN/includes/css/PAGENAME.css`
- `/zc_plugins/plugin_path...../admin/includes/css/global_stylesheet.css`
- `/zc_plugins/plugin_path...../admin/includes/css/PAGENAME.css`
- `/YOURADMIN/includes/css/PAGENAME_*.css` (note the `_`, followed by additional characters) **(THIS IS WHERE YOU PUT YOUR CUSTOM CSS)**

It is a good practice to put your own page-specific customizations into a non-core file 
(eg: `pagename_mystore.css`) so that there are fewer file conflicts when upgrading.

Plugins not using the `zc_plugins` structure should put their page-specific CSS additions into a file using a naming convention akin to: `pagename_pluginname.css`


## Per-Page JS Files

You may put your custom JavaScript for individual Admin pages into page-specific files that will automatically load on those pages.

The convention (and loading order) is:

- `/YOURADMIN/includes/javascript/PAGENAME.js`
- `/YOURADMIN/includes/javascript/PAGENAME.php`
- `/zc_plugins/plugin_path...../admin/includes/javascript/global_jscript.php`
- `/zc_plugins/plugin_path...../admin/includes/javascript/global_jscript.js`
- `/zc_plugins/plugin_path...../admin/includes/javascript/PAGENAME.php`
- `/zc_plugins/plugin_path...../admin/includes/javascript/PAGENAME.js`
- `/zc_plugins/plugin_path...../admin/includes/javascript/PAGENAME_*.php`  (note the `_`, followed by additional characters)
- `/zc_plugins/plugin_path...../admin/includes/javascript/PAGENAME_*.js`  (note the `_`, followed by additional characters)
- `/YOURADMIN/includes/javascript/PAGENAME_*.js` (note the `_`, followed by additional characters)
- `/YOURADMIN/includes/javascript/PAGENAME_*.php` (note the `_`, followed by additional characters)

It is a good practice to put your own page-specific customizations into a non-core file 
(eg: `pagename_mystore.js`) so that there are fewer file conflicts when upgrading.

Plugins not using the `zc_plugins` structure should put their page-specific custom JavaScript into a file using a naming convention akin to: `pagename_pluginname.js`

## Site Specific Overrides 

Starting in Zen Cart 1.5.8, an [admin site-specific override](/user/admin/site_specific_overrides/) capability exists. 

## Related 

- [Customizing your Admin](/user/customizing/admin_customizing)

