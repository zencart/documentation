---
title: Turning sidebox display off/on on an EZ-Page
description: I don't want sideboxes to show on my EZ-Pages
category: ezpages
weight: 10
---

You may wish to have sideboxes display on regular pages (such as the shopping cart page or the checkout shipping page) but not on an EZ-Page.  This can be done using the instructions below. 

To do this you will need to edit the sidebox module for each of the sideboxes whose behavior you wish to change. The exact change will depend upon what exactly you wish to do and whether those sideboxes should appear on other pages. Let's assume that your objective is to selectively suppress the display of sideboxes on some EZ-Pages.  

You can find your sidebox modules in the directory includes/modules/sideboxes/. Towards the bottom of each is a block of code similar to this one  

```
    $title =  BOX_HEADING_CUSTOMER_ORDERS;
    $title_link = false;
    require($template->get_template_dir($column_box_default,  DIR_WS_TEMPLATE, $current_page_base,'common') . '/' .  $column_box_default);
```

You will need to wrap this in a conditional statement such as  

```
if (!isset($ezpage_id) || !in_array($ezpage_id,explode(",",'2,5'))) {
    require($template->get_template_dir('tpl_order_history.php',DIR_WS_TEMPLATE,  $current_page_base,'sideboxes'). '/tpl_order_history.php');
    $title =  BOX_HEADING_CUSTOMER_ORDERS;
    $title_link = false;
    require($template->get_template_dir($column_box_default,  DIR_WS_TEMPLATE, $current_page_base,'common') . '/' .  $column_box_default);
}
```

This condition means that the template to display the sidebox will be called whenever the page is not an EZ-Page or, if it is an EZ-Page, it does not have ID 2 or 5. You can find the IDs of your EZ-Pages by going to [Admin > Tools > EZ-Pages](/user/admin_pages/tools/ezpages/) where the ID for each page is displayed in the first column.  

Finally, and importantly, don't forget to save your result in [an override file](/user/new_user_topics/overrides/).

Another way to do this is [turning off columns entirely](/user/template/left_right_columns/).
