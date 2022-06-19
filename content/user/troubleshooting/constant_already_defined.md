---
title: Constant already defined debug logs 
description: How to suppress logs saying a constant is already defined 
category: troubleshooting 
weight: 10
---

[Debug logs](/user/troubleshooting/debug_logs/) like this: 

```
--> PHP Warning: Constant TEXT_MAIN already defined in /Users/scott/Sites/store/includes/languages/english/index.php on line 9.
```

occur when a PHP `define` statement is used twice for the same constant.  The root cause of this issue is addressed in Zen Cart 1.5.8, but until then, storeowners using Zen Cart 1.5.7 can suppress this message using the following method: 

- Go to Admin > Configuration > Logging 
- Set `Report All Errors (Admin)?` and `Report All Errors (Store)?` to `IgnoreDups`.


