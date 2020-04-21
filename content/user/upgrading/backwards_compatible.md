---
title: Not Backwards Compatible Changes
description: Not Backwards Compatible Changes to Zen Cart 
category: Upgrading
weight: 10
---

This document lists changes to the database schema or contents which deserve special notice, since they can break things in subtle ways.  They are listed in release order, descending.

### Zen Cart 1.5.7 

- The configuration constant `UPLOAD_FILENAME_EXTENSIONS` was removed from the database and replaced with an entry in `includes/classes/upload.php`.   If you have modified this constant from its original setting of `jpg,jpeg,gif,png,eps,cdr,ai,pdf,tif,tiff,bmp,zip` you will want to make the same change in the aforementioned file. 

### Zen Cart 1.5.6 

In 1.5.6, the variable `$downloads`, returned from `includes/modules/downloads`, changed from a query result to an array.  Accordingly, templates which use this file will need to be adjusted to process an array rather than a database query. 

### Zen Cart 1.5.0 

- The admin menus are no longer built by files ending in `.dhtml`.  Instead, a new database table called `admin_pages` was introduced.  Mods which create their own menu entries must also follow this convention.  Guidelines for [upgrading plugins to 1.5](/dev/plugins/upgrading_to_1.5) include instructions on this step.
