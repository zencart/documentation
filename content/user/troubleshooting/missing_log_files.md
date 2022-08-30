---
title: Missing Log Files 
description: What if Zen Cart does not write to the /logs folder?
category: troubleshooting
weight: 10
---

By default, Zen Cart writes debug logs into a folder called `/logs` at the root of the store.

However, in some hosting environments like [PHP-FPM shared](/user/running/fpm/), error logs are not written individually to the `/logs` folder. 

For example, some hosts that use PHP-FPM configure logging to go to a single central file.  

So instead of creating individual log files in 
`/home/YOURACCOUNT/public_html/logs/` 

They append to a single log file, which is stored in 

`/home/YOURACCOUNT/logs/YOURSITE_com.php.error.log`

If you are missing log files, you'll want to work with your hoster to see how 
they have configured logging. 

You can determine if your host has you configured to run PHP-FPM by 
following the guidelines on the [PHP-FPM](/user/running/fpm/) page.

