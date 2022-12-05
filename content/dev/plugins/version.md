---
title: Zen Cart Version Checking in your Plugin 
description: Determining which version of Zen Cart you are running
category: plugins
weight: 10
---

The function `zen_get_zcversion` was created for this purpose. 

For example, to determine if you're running Zen Cart 1.5.7 or higher, use 

```
if (function_exists('zen_get_zcversion') && zen_get_zcversion() >= '1.5.7') { 
``` 

If you need to check for lower versions, use the defines from `includes/version.php`.

For example, if your code only runs on Zen Cart 1.5.6, use something like 

```
if (PROJECT_VERSION_MAJOR != '1' && substr(PROJECT_VERSION_MINOR, 0, 3) == '5.6') { 
  // you are running 1.5.6-1.5.6c  
}
```

In some cases, it might make more sense to use `function_exists`.  For example, in Zen Cart 1.5.8, several functions were renamed.  To determine which function to call, rather than checking for the Zen Cart version, you could do something like this: 

```
      if (function_exists('zen_draw_pulldown_products')) {
         echo zen_draw_pulldown_products(...); 
      } else {
         // 1.5.7 and below
         echo zen_draw_products_pull_down(...); 
      }
```

