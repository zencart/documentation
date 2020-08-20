---
title: Display the search box in the header only 
description: How to put the search box at the top of the page 
category: sideboxes
weight: 10
---

There are two sideboxes for search.  You can control both through the [Admin > Tools > Layout Box Controller](/user/admin_pages/tools/layout_boxes_controller/).


The `search.php` sidebox is a conventional sidebox and can be turned on and off as normal. If you want search in the header, you will normally turn this sidebox off, though it does have the advantage of providing a link to the advanced search page.

![search.php](/images/sidebox_search.png)

<br><br>

The `search_header.php` sidebox is specifically designed to display a search box in your Zen Cart header and so doesn't output all the HTML needed for a sidebox. It is recommended therefore that you ensure that its left/right column status is set to OFF. To display it in the header, set the single column status to ON.

![search.php](/images/sidebox_search_header.png)
