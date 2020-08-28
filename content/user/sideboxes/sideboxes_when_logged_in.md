---
title: Displaying sideboxes for logged in visitors only
description: Customizing sidebox display based on customer status 
category: sideboxes
weight: 10
---

Displaying a specific sidebox only for logged in customers can be done with the following steps:

1. Locate the module for the sidebox (or boxes) that you want to treat like this. You'll find them in `includes/modules/sideboxes`.

2. Create override files for them by copying them to `
includes/modules/sideboxes/YOURTEMPLATE`.

3. Open the override file and find a couple of lines that look similar to

```
// test if box should display
$show_featured= true;
```

These were taken from the featured_products products sidebox and the variable name for your box will probably differ slightly. Then change them to

```
// test if box should display
if (!$_SESSION['customer_id']) {
$show_featured= false;
} else {
$show_featured= true;
}
```

4. Upload to your server and enjoy.

