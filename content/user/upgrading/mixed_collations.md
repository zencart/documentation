---
title: Mixed Collation Errors 
description: How to handle "Illegal mix of collations" after upgrade 
category: upgrading 
weight: 10
---

If you are getting PHP log files that say things like: 

```
Illegal mix of collations (latin1_general_cs,IMPLICIT) and (latin1_general_ci,IMPLICIT) for operation '='
```

the easiest way to fix this is to simply convert your database to use UTF8.  Fortunately there is a [UTF8 Conversion Tool](/user/upgrading/convert_to_utf8/) you can run to do this. 


