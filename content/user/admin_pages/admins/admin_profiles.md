---
title: Admin Profiles 
category: admin_pages
weight: 10
---

The capabilities of an administrator in Zen Cart are limited by the _profile_ for that account.  The available profiles are shown on this screen (Admins > Admin Profiles).  

![Admin Profiles](/images/profiles.png)


The profile for each administrator can be seen in the [Admins > Admin Users](/user/admin_pages/admins/admin_users/) screen.  A profile is assigned to an administrator account when it is created. 

![Admin Users](/images/admin_users_2.png)

The `Superuser` profile has access to all the functions in admin.

All other profiles have access to a subset of functions, which is defined by 
their admin profile. 

When the database is created (or upgraded to the latest release), the 
profile *Order Processing* is created as an example.  This profile
has access to a subset of the `Customers`, `Reports` and `Discounts` menus, 
but not to the `Configuration` or `Catalog` menus.  Of course you can 
customize this to your needs or create new profiles that match your 
requirements.  

Remember to review your admin profiles 
as you add new functions to your admin.  For example, if you 
install [Edit Orders](/user/orders/edit_orders/), 
although your `Order Processing` profile can run all the standard functions 
under `Admin > Customers`, they still can't run Edit Orders until you go 
to `Admin > Admins > Edit Profiles` and check the *Edit Orders* box. 

<br />
<img src="/images/admin_profiles.png" alt="Zen Cart Admin Profiles" />
<br /><br />

**Note:** If you don't see an item in this list that does appear on the Superuser admin menu, review the troubleshooting instructions in  [Admin menu item is missing](/user/troubleshooting/admin_menu_item_missing/).
