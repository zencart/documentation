---
title: How do I find the value of a configuration setting? 
description: Where are the all-uppercase strings set? 
category: template
weight: 10
---

If you're modifying a template and you want to check a config value, you can 
look at the [All Configuration Settings](/user/admin_pages/configuration/all/) page 
and do a search for the configuration title.  The configuration key will be 
shown when you find it, and you can use that in your code.  The configuration
key is created as a defined constant as part of the initialization code. 

Example: You want to display the value of the email address that emails
are sent from.  

Go to the page linked above, and search for `sent FROM`.  You'll see that the 
configuration key is `EMAIL_FROM`.   It's a defined constant so it doesn't 
need a `$`. 

```
<?php
echo "We welcome your feedback - just email " . EMAIL_FROM . ".<br />"; 
```

Conversely, if you're modifying a template, you might see a config like 
`SHOW_TOTALS_IN_CART`.
If you want to know where it is set, 
look at the [All Configuration Settings](/user/admin_pages/configuration/all/) page, 
and search for it. 
When you see it, look back up to the last header, you'll see it's in 
`Configuration > Layout Settings`, so now you know where it is set.

If you have an all uppercase value referenced in your template, and you don't see the value in configuration settings, it's likely a language string. 
