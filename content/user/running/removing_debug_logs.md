---
title: Removing debug logs 
description: How do I clean out debug logs? 
category: Running
weight: 10
---

You can purge most of the [debug logs](/user/troubleshooting/debug_logs/) that Zen Cart produces from the [Store Manager](/user/admin_pages/tools/store_manager/).

But what if your cart has debug logs from a plugin or other modification? 

Modify `admin/store_manager.php` and look for `case 'clean_debug_files':`.

You'll see the regular expression that identifies debug logs. Add an entry for your particular log. 
