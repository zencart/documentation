---
title: Suppressing sidebox display on specific pages 
description: Customizing sidebox display based on page 
category: sideboxes
weight: 10
type: codepage
---

**Example 1**: I want to display the featured sidebox on my front page only, and suppress it from all other pages.

Create an override for the sidebox's module file. For the featured products sidebox, this would involve copying `includes/modules/sideboxes/featured_products.php` to `includes/modules/sideboxes/YOURTEMPLATE/featured_products.php`.  

Open up your new sidebox module file and take a look at the code. 
Generally it will look something like this  

```
<?php  

BIG COMMENT BLOCK  

// test if box should display  
  $show_featured= true;  

  if ($show_featured == true) {  

    // MAIN PROCESSING BLOCK  

  }  
?>
```

All we need to do is to change the line that reads  

```
$show_featured= true;
```

into  

```
  if ($this_is_home_page) {  
    $show_featured = true;  
  } else {  
    $show_featured = false;  
  }
```

If your sidebox module doesn't have a conditional such as 
`if ($show_featured == true) { ... } ` wrapped around the code, then just add it (changing the variable name to something suitable and unique for your sidebox to avoid unintentionally turning off other sideboxes).

**Example 2**: I do not want to display any sideboxes on the checkout pages. 

Modify the file `includes/templates/YOURTEMPLATE/common/tpl_main_page.php`.

Add this after the comment block at the top of the file: 

```
if (in_array($current_page_base,explode(",",'checkout_shipping,checkout_payment,checkout_confirmation,checkout_success')) ) {
  $flag_disable_right = true;
  $flag_disable_left = true;
}
```

**Example 3**: I want all the sideboxes on the right removed.

Turning off each of the sideboxes set to display on the right in 
[Admin > Tools > Layout Boxes Controllers](/user/admin_pages/tools/layout_boxes_controller/) is not enough.  You need to reclaim the space by going to 
[Admin > Configuration > Layout Settings](/user/admin_pages/configuration/configuration_layoutsettings/) and  setting *Column Right Status - Global* to 0. 

