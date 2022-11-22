---
title: Zen Cart Version Checking in your Plugin 
description: Determining which version of Zen Cart you are running
category: plugins
weight: 10
---

The function `zen_get_zcversion` was created for this purpose. 

For example, to determine if you're running Zen Cart 1.5.8 or higher, use 

```
if (function_exists('zen_get_zcversion') && zen_get_zcversion() >= '1.5.8') { 
``` 

If you need to check for lower versions, use the defines from `includes/version.php`.

For example, if your code only runs on Zen Cart 1.5.6, use something like 

```
if (PROJECT_VERSION_MAJOR != '1' && substr(PROJECT_VERSION_MINOR, 0, 3) == '5.6') { 
  // you are running 1.5.6-1.5.6c  
}
```

