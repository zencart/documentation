---
title: FPM 
description: What is FPM? 
category: running 
weight: 10
---

You can determine if your host has you configured to run PHP-FPM by looking at the 
[Server/Version Info](/user/admin_pages/tools/server_info) page, under the **cgi-fcgi** section.  

(Note: If you don't see the line that says "php-fpm active," then it's not active.)

![FPM](/images/fpm.png)

If PHP-FPM is active, look under the **Core** section to determine where your log is stored:

![FPM Log](/images/fpm_log.png)

Running FPM has a couple of side effects you should be aware of:

- [Caching](/user/new_user_topics/browser_caching/) web pages
- Changes to how [logging](/user/troubleshooting/missing_log_files/) works. 

