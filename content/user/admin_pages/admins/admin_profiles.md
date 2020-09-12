---
title: Admin Profiles 
category: admin_pages
weight: 10
---

The capabilities of an administrator in Zen Cart are limited by the _profile_ for that account.  The profile for each administrator can be seen in the [Admins > Admin Users](/user/admin_pages/admins/admin_users/) screen.  A profile is assigned to an administrator account when it is created. 

The `Superuser` profile has access to all the functions in admin.
Admin Profiles allows you to create classes of administrators that have
access to a subset of all admin functions.  

When the database is created (or upgraded to the latest release), the 
profile *Order Processing* is created as an example.  This profile
has access to a subset of the `Customers`, `Reports` and `Discounts` menus, 
but not to the `Configuration` or `Catalog` menus.  Of course you can 
customize this to your needs or create new profiles that match your 
requirements.  

One thing to remember is that the admin profiles you create need to be 
maintained as you add new functions to your admin.  For example, if you 
install [Edit Orders](https://www.zen-cart.com/downloads.php?do=file&id=1513), 
although your `Order Processing` profile can run all the standard functions 
under `Admin > Customers`, they still can't run Edit Orders until you go 
to `Admin > Admins > Edit Profiles` and check the *Edit Orders* box. 

<br />
<img src="/images/admin_profiles.png" alt="Zen Cart Admin Profiles" />
<br /><br />

