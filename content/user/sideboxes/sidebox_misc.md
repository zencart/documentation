---
title: Miscellaneous Sidebox Questions 
category: sideboxes
weight: 2 
---

{{< misc >}} 

--- 

### How do I enable/disable sideboxes on EZ-Pages? 
See the [sidebox display changes](/user/ezpages/sidebox_display_changes/) FAQ. 

---
### How do I remove and/or re-arrange the sideboxes?
See [the rearranging sideboxes](/user/template/remove_rearrange_sideboxes/) FAQ.

---
### How do I add images to a sidebox? 
See [the images in sideboxes](/user/template/add_image_box/) FAQ. 

---
### How do I remove "Page 1", "Page 2" and "Page 3" from my More Information sidebox?
Go to Admin > Configuration > Define Page Settings and set their values to 2 or 3.

---
### How do I change the a sidebox title?

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


---
<!-- please keep this at the end --> 
{{< faq_questions >}}
