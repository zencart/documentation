---
title: Zen Cart Version Checking in your Plugin 
description: Determining which version of Zen Cart you are running
category: plugins
weight: 10
---

The function `zen_get_zcversion` was created for this purpose. 

For example, to determine if you're running Zen Cart 1.5.8 or higher, use 

```
if (zen_get_zcversion() >= '1.5.8') { 
``` 
