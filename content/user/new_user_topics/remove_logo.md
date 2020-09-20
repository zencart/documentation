---
title: How do I remove the logo completely? 
description: I don't want a logo for my site 
category: new_user_topics
weight: 10
---

If you don't want or need a logo, open `includes/templates/YOURTEMPLATE/common/tpl_header.php`, and find and remove this line of code 

``` 
<div id="logo">
<?php // echo '<a href="' . HTTP_SERVER . DIR_WS_CATALOG . '">' . zen_image($template->get_template_dir(HEADER_LOGO_IMAGE, DIR_WS_TEMPLATE, $current_page_base,'images'). '/' . HEADER_LOGO_IMAGE, HEADER_ALT_TEXT) . '</a>'; ?>
</div>
```

