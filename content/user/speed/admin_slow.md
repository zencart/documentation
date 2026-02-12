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

### Page Specific Slowness 

1. If the slowness is on the Admin > Catalog > Category/Products page, try making these two config changes: 

- Admin > Configuration > My Store > Show linked status for categories = false 
- Admin > Configuration > My Store > Show Category Counts - Admin = false

2. If the slowness is on the Admin > Customers > Customers page, see if there are unused customer accounts that can be deleted (by [Delete Spam Customers](https://www.zen-cart.com/downloads.php?do=file&id=2253), for example).

3. If the slowness is on the Admin > Customers > Orders page, look at some of the [Admin Setting Overrides](/user/admin/site_specific_overrides/) that can be done to speed up that page (notably `$quick_view_popover_enabled` and `$includeAttributesInProductDetailRows`).

### Software Changes to consider 
Sometimes one of the widgets on the dashboard is the cause of the slowness.  You can tweak these to improve performance at the cost of less functionality.  These are things you can try: 

In 1.5.8 or above: 
- Use the [Admin Site Specific Overrides](/user/admin/site_specific_overrides/) file, and set `$includeAttributesInProductDetailRows` and `$includeAttributesInPopoverRows` to false.  You may also lower `$recentOrdersMaxRows` in this same file to show fewer new orders on the dashboard.


In 1.5.7 or below: 
- modify `admin/includes/modules/dashboard_widgets/RecentOrdersDashboardWidget.php` and set `$includeAttributesInPopoverRows` to `false`.

- modify `admin/orders.php` and set `$includeAttributesInProductDetailRows` to `false`. 


You may also wish to disable specific widgets by modifying `admin/index_dashboard.php`.  See [Admin Dashboard - Customizing](/user/admin_pages/admin_dashboard/#customizing).


### Disabling Plugin Version Checks
Some plugins [call the Zen Cart server to check for a new version](/dev/plugins/tips/#automatic-new-version-checks).  You can disable this behavior - see [How do I disable plugin version checking?](/user/plugins/version_check).

