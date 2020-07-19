---
title: Auto Inclusion System
description: Zen Cart Auto Inclusion System
category: code
weight: 10
---

To reduce the number of changes required for plugin authors, Zen Cart does some automatic inclusion of files. 

### Functions 
<<<<<<< HEAD
Any `*.php` files placed in `includes/functions/extra_functions` are loaded automatically, and can be called by any storefront side logic.  Similarly, on the admin side, functions in `admin/includes/functions/extra_functions` are automatically loaded. 
=======
Any functions placed in `includes/functions/extra_functions` are loaded automatically, and can be called by any storefront side logic.  Similarly, on the admin side, functions in `admin/includes/functions/extra_functions` are automatically loaded. 
>>>>>>> fe0f67393dbd6c28d2cd1a325c21e64b1f2ae9ba

### Language Files 

- A storefront side page will automatically load its own language file.  So the page `includes/modules/pages/contact_us/` will load `includes/languages/english/contact_us.php`
- All files in `includes/languages/english/extra_definitions` are automatically loaded.

### Extra Datafiles and Extra Configures 

Any `*.php` files in this folder are loaded automatically. 

### Extra Cart Actions 

Any `*.php` files in this folder are loaded automatically. 

### Auto Loaded Observers 

These are described in the [Notifiers and Observers](/dev/code/notifiers/#auto-loaded-observers) documentation.  Files in `includes/classes/observers` whose name begins with `auto` and which define a class named **zcObserver** + the [CamelCased](http://en.wikipedia.org/wiki/CamelCase) filename. 

### Stylesheets 

A number of stylesheets are automatically loaded; this process is described in the [stylesheet documentation](/user/template/stylesheet/). 

