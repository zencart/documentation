---
title: Admin is slow or hangs forever 
description: Dealing with performance issues in Admin 
category: speed
weight: 10
---

**NOTE:** Is the slowness *only* for the admin area? If you also see the *same* slowness in your storefront, this FAQ does not apply to your situation.

When you first log in to the Admin area, Zen Cart attempts to talk to the Zen Cart versioning server to see if updates are available. If it can't communicate with the versioning server then it is possible that you'll see your admin access hang for a minute or so.

There are 2 approaches to addressing this:

1. When you DO log into the admin area, turn off version checking here:
[Admin > Configuration > My Store](/user/admin_pages/configuration/configuration_mystore/), and set `Show if version update available` to false. 



2. IF AND ONLY IF you can't log into the admin area AT ALL, try editing the `/admin/includes/local/skip-version-check.ini` file and disable version checking: 

```
version_check=off
```

### Other settings that can cause slowdowns
In addition to the settings mentioned above, additional settings you may wish to change to improve admin performance are as follows:

- Admin > Configuration > My Store > Show if version update available
- Admin > Configuration > Email > Audience-Select Count Display

Each of these settings has its own documentation.

### Software Changes to consider 
Sometimes one of the widgets on the dashboard is the cause of the slowness.  You can tweak these to improve performance at the cost of less functionality.  These are things you can try: 

In 1.5.8 or above: 
- Use the [Admin Site Specific Overrides](/user/admin/site_specific_overrides/) file, and set `$includeAttributesInProductDetailRows` and `$includeAttributesInPopoverRows` to false.


In 1.5.7 or below: 
- modify `admin/includes/modules/dashboard_widgets/RecentOrdersDashboardWidget.php` and set `$includeAttributesInPopoverRows` to `false`.

- modify `admin/orders.php` and set `$includeAttributesInProductDetailRows` to `false`. 


You may also wish to disable specific widgets by modifying `admin/index_dashboard.php`.


