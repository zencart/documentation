---
title: Missing Log Files 
description: What if Zen Cart does not write to the /logs folder?
category: troubleshooting
weight: 10
---

In some hosting environments (notably PHP-FPM shared), error logs are not written individually to the `/logs` folder. 

For example, some hosts configure logging to go to a single central file.  

So instead of creating individual log files in 
`/home/YOURACCOUNT/public_html/logs/` 

They append to a single log file, which is stored in 

`/home/YOURACCOUNT/logs/YOURSITE_com.php.error.log`

If you are missing log files, you'll want to work with your hoster to see how 
they have configured logging. 

