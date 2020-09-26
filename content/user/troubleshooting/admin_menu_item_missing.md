---
title: Admin menu item is missing
description: I can't find an item in my Admin menu
category: troubleshooting 
weight: 10
---

Admin menu items are controlled by two factors:

1. Profile Permissions

   If you are logged into Admin with a user whose profile doesn't have access to that page, then the menu option won't display for you.
   
   See [Admin Profiles](/user/admin_pages/admins/admin_profiles/) for more information.

2. Text strings defined to display the item

Menu options don't display if the `FILENAME_` or `BOX_` constants for them aren't defined.

These constants are defined in various places:

- `/includes/filenames.php` (for core system files, not plugins)
- `/admin/includes/languages/english.php` (for core system files, not plugins)
- `/admin/includes/extra_datafiles/*.php` (for plugins)
- `/admin/includes/languages/english/extra_definitions/*.php` (for plugins)

(And for other languages, consult the corresponding language directories/files.)

