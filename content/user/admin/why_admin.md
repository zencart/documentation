---
title: Why is the Admin area so busy? 
description: Why so many options?  Also, where's the feature *I* want? 
category: admin
weight: 5
---

The obvious reason Zen Cart admin exists is so that storeowners have a web interface to order processing and stock management.

A somewhat less obvious reason is to permit some configuration actions to be done via an admin panel, rather than needing to modify code.

Plugin authors sometimes take shortcuts and advise users to modify a file to tune the behavior of a plugin.  The Zen Cart team deliberately extracted some of those customization choices and put them into an admin panel, so that storeowners can do this by themselves and not need to depend on a developer. 

*This is a tricky balance!*  Many of the same people who complain that the admin has too many menus and options will also complain that there's no admin switch for the option _they_ want. 

Every setting in the admin is an aspect you can change in your store without needing to modify code.
Zen Cart is designed to be storeowner-friendly in the sense that you can customize your cart without being a software developer.

At the same time, every setting in the admin is yet another thing the storeowner must read when trying to find something.  So some settings are deliberately left out of the configuration, and hard coded instead. 

We have attempted to mitigate the complexity of the admin by providing 
[documentation for each of the configuration screens](/user/admin_pages/configuration/). 
There's even a way to [view all configuration settings](/user/admin_pages/configuration/all/) on a single page. 

Although Storeowners with Superuser accounts have to live with a large admin panel, accounts for staff can be set up with custom [Admin Profiles](/user/admin_pages/admins/admin_profiles/) that only show relevant menus.  

