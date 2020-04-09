---
title: Admin Profiles 
description: Zen Cart Admin Profiles Admin Page 
category: admin_pages
weight: 10
---

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

