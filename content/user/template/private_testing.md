---
title: Privately testing a new template 
description: Allowing an admin test a new template on a live site 
category: template
weight: 10
---

It is possible for an admin user to privately test a new template while other users see the regular template.  Use these steps: 

-  Determine your IP Address
-  Go to the screen Admin > Configuration > Website Maintenance, and enter your IP Address in the *Down For Maintenance (exclude this IP-Address)* field. 
-  Visit the storefront and append `t=YOURNEWTEMPLATE` to the URL.  You will now be locally switched to the new template. 
- When you're finished testing, append `t=off` to the URL.
