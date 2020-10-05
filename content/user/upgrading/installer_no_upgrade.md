---
title: Installer does not show an Upgrade button
description: I only see the Clean Install button
category: upgrading 
weight: 10
---

If you have begun the upgrade process by going to `YOURSITE.com/zc_install`, but you don't see an **Upgrade ...** button, it means the system can't recognize your existing database.  Look at your `includes/configure.php` file and check these things: 

- Is the `DB_DATABASE` the correct name for the database you are importing? 
- Does `DB_PREFIX` correctly reflect the prefix used on the tables in the database? 

When everything is configured correctly, you should see this at the bottom of the screen on the first page of `zc_install`: 

![Use the upgrade button!](/images/upgrade_button.png)
