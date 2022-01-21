---
title: Privately testing a new template 
description: Allowing an admin test a new template on a live site 
category: template
weight: 10
---

In recent versions of Zen Cart, it is possible for an admin user to privately test a new template while other users see the regular template.  Use these steps: 

-  Determine your IP Address
-  Go to the screen Admin > Configuration > Website Maintenance, and enter your IP Address in the *Down For Maintenance (exclude this IP-Address)* field. 

**NOTE:** If you are using a local webserver (such as MAMP or WAMP), you must use whatever value is contained in `$_SERVER['REMOTE_ADDR']` for your IP Address.  This will *not*  be your public facing IP address - it might be `::1` or some other private value. 

-  Visit the storefront and append the argument `t=YOURNEWTEMPLATE` to the URL.  You will now be locally switched to the new template. 

For example, if the URL was 

```
https://MYSTORE.com/index.php
```

you would use 

```
https://MYSTORE.com/index.php?t=MYTEMPLATE
```

If the URL was 

```
https://MYSTORE.com/index.php?main_page=index&cPath=6
```

you would use 

```
https://MYSTORE.com/index.php?main_page=index&cPath=6&t=MYTEMPLATE 
```

- This only needs to be done once; it will be carried forward for subsequent page visits in the current session. 

- When you're finished testing, append `t=off` to the URL to stop private testing.

If you want to make other templates available to all users (i.e. not limit it to IP addresses from the Down For Maintenance list), make the following changes: 

- copy `includes/init_includes/init_templates.php` to `includes/init_includes/overrides/init_templates.php`
- At the bottom of `includes/init_includes/overrides/init_templates.php`

change 
```
if (zen_is_whitelisted_admin_ip()) {
```
to

```
if (1) {
```
