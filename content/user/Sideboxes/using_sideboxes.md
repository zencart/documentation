---
title: Using Sideboxes 
category: sideboxes
weight: 1
---

Miscellaneous Questions about Sideboxes 

### How do I remove "Page 1", "Page 2" and "Page 3" from my more information sidebox?
Go to Admin > Configuration > Define Page Settings and set their values to 2 or 3.

### How do I re-arrange the order of the links in the information sidebox?

1. Create (if you don't already have it) a directory named `includes/modules/sideboxes/YOURTEMPLATE/`

2. Copy the includes/modules/sideboxes/information.php file into your new directory

3. Edit the `if` blocks into the order that you would like them to appear.

For example, if you wished the terms and conditions link to appear first, you would move this entire block of php:

<pre>
  if (DEFINE_CONDITIONS_STATUS <= 1) {
    $information[] = '<a href="' . zen_href_link(FILENAME_CONDITIONS) . '">' . BOX_INFORMATION_CONDITIONS . '</a>';
  }
</pre>

 (taking care not to leave the curly bracket behind) to just below the line that says:
<pre>
  unset ($information);
</pre>
