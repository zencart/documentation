---
title: Is there a way that I can check on what users with Admin access to my site are doing?
description: Monitoring admin users 
category: admin
weight: 10
---

Each time an Admin page is called, the access date, admin ID, page accessed, page parameters and IP address are logged in the `admin_activity_log` table. The contents of this table can be viewed via database management tools such as `phpMyAdmin`.  The table may also be exported using [Admin > Admins > Admin Activity Logs](/user/admin_pages/admins/admin_activity_logs/). 

You can also limit the scope of any admin user's capabilities using the [Admin Profiles](/user/admin_pages/admins/admin_profiles/) feature.

