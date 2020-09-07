---
title: How can I disable "search in description" in the search sidebox?
description: Narrowing search fields to exclude products_description 
category: search 
weight: 10
---

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

