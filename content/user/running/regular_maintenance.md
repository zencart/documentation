---
title: Regular Periodic Maintenance 
description: What you should do to keep your store running well 
category: Running
weight: 1
---

This is a partial list of regular maintenance activities you should do on your store.  You will want to to do these things between once a week and once a month, depending on how busy your store is. 

- Make a [database backup](/user/running/backup/).
- Handle [old admin activity logs](/user/admin_pages/admins/admin_activity_logs/) - archive them first, then purge them.
- Investigate any [debug logs](/user/troubleshooting/debug_logs/) which are present in your `/logs` folder.  If you are unfamiliar with handling debug logs, [read this first](/user/troubleshooting/blank_page/#working-with-debug-logs).
- Check to see if there is a [new Zen Cart version available](/user/admin_pages/admin_new_version_available/).  If there is, schedule your [upgrade](/user/upgrading/) to be sure you can get it done soon. It's also a good practice to keep track of [the PHP Version Support Policy](https://www.php.net/supported-versions.php) so you know when the [PHP version you are running](/user/admin_pages/admin_version/) is at or near end of life.
- Check your SSL certificate - they do expire and need to be renewed once a year.  If there's a glitch (like your credit card expiring), you will have the dreaded [broken padlock](/user/running/broken_padlock/) issue.
- Optional: Run "Optimize Database" from [Admin > Tools > Store Manager](/user/admin_pages/tools/store_manager/). 

