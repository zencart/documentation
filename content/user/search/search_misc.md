---
title: Miscellaneous Search Questions 
description: Searching in Zen Cart 
category: search 
weight: 2 
---

{{< misc >}} 

--- 
### I want the search box in my site header.  How do I do that? 


See [How do I display the search box in the header only?](/user/sideboxes/search_box_header_only/)

---

### How can I disable "search in description" in the search sidebox? 

For the regular sidebox search, make the following change: 

Edit `includes/templates/YOURTEMPLATE/sideboxes/tpl_search.php` and change 

```
$content .= zen_draw_hidden_field('search_in_description', '1') . zen_hide_session_id();
```

to

```
$content .= zen_hide_session_id();
```

For the header sidebox search, make the same change, but in `includes/templates/YOURTEMPLATE/sideboxes/tpl_search_header.php`. 


---
<!-- please keep this at the end --> 
{{< faq_questions >}}
