---
title: How do I change the a sidebox title?
description: Where are the strings for sidebox titles? 
category: sideboxes
weight: 10
---

Look in `includes/languages/YOURTEMPLATE/english.php`. 
Suppose you want the Categories sidebox to have a different title. Look for

```
define('BOX_HEADING_CATEGORIES', 'Categories');
```

Changes for other sideboxes will follow this pattern:

```
define('BOX_HEADING_XXXXXXXX', 'New Title');
```

Where `XXXXXXXX` is the name of the sidebox. 

Make the needed changes. Be sure that the single quote marks are not left out.

