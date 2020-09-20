---
title: Admin is slow or hangs forever 
description: Dealing with performance issues in Admin 
category: performance
weight: 10
---

**NOTE:** Is the slowness *only* for the admin area? If you also see the *same* slowness in your storefront, this FAQ does not apply to your situation.

When you first log in to the Admin area, Zen Cart attempts to talk to the Zen Cart versioning server to see if updates are available. If it can't communicate with the versioning server then it is possible that you'll see your admin access hang for a minute or so.

There are 2 approaches to addressing this:

1. When you DO log into the admin area, turn off version checking here:
[Admin > Configuration > My Store](/user/admin_pages/configuration/configuration_mystore/), and set `Show if version update available` to false. 



2. IF AND ONLY IF you can't log into the admin area AT ALL, try editing the `/admin/includes/local/skip-version-check.ini` file and disable version checking: 

```
version_check=off
```

