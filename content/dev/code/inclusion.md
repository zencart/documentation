---
title: Auto Inclusion System
description: What files are automatically included? 
category: code
weight: 10
---

To reduce the number of changes required for plugin authors, Zen Cart does some automatic inclusion of files. 

### Functions 
Any `*.php` files placed in `includes/functions/extra_functions` are loaded automatically, and can be called by any storefront side logic.  Similarly, on the admin side, functions in `admin/includes/functions/extra_functions` are automatically loaded. 

### Language Files 

- A storefront side page will automatically load its own language file.  So the page `includes/modules/pages/contact_us/` will load `includes/languages/english/contact_us.php`
- All files in `includes/languages/english/extra_definitions` are automatically loaded.

### Extra Datafiles, Extra Configures, Extra Cart Actions 

Any `*.php` files in this folder are loaded automatically. 

See [Extra folders](/dev/code/extra_folders/) for a complete list. 

### Auto Loaded Observers 

These are described in the [Notifiers and Observers](/dev/code/notifiers/#auto-loaded-observers) documentation. Auto-loaded Observer files include those in `includes/classes/observers` (and Admin) whose name begins with `auto.` and which define a class named **zcObserver** + the [CamelCased](http://en.wikipedia.org/wiki/CamelCase) filename - for example, `class zcObserverFooObserver`. 

### Stylesheets 

A number of stylesheets are automatically loaded; this process is described in the [stylesheet documentation](/user/template/stylesheet/). 

