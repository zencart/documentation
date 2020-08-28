---
title: Left and Right Columns - turning them off 
description: Three columns, two, or one - your choice 
category: template
weight: 10
---

### Turning off a column on specific pages 

Firstly, if you don't already have one, create an override file for tpl_main_page.php in your `includes/templates/YOURTEMPLATE/common` directory.  

There is enormous scope within this one module to create turn the left and right hand columns on and off according to which page is to be displayed. Open it up and you will see a large comment at the top explaining some of them. Here are a few examples to help illustrate that.

If you wish to turn off the left hand column for the "contact us" and "terms & conditions" pages, find the following block of code  

```
if (in_array($current_page_base,explode(",",'list_pages_to_skip_all_right_sideboxes _on_here,separated_by_commas,and_no_spaces')) ) {  
     $flag_disable_right = true;  
  }
```

and edit it to read  

```
if (in_array($current_page_base,explode(',','contact_us,conditions')) ) {  
     $flag_disable_left = true;  
  }
```

If you wished to disable both columns during checkout, add or edit the above block to read  
```
if (in_array($current_page_base,explode(',','checkout_shipping,checkout_payment,checkout_confirmation')) ) {  
    $flag_disable_right = true;  
    $flag_disable_left = true;  
  }
```

To disable the right column for EZ-Pages 2 and 5, 

```
if (isset($ezpage_id) && in_array($ezpage_id,explode(",",'2,5'))) {  
    $flag_disable_right = true;  
  }
```

To turn off the left column for the home page only, you would insert the following:  

```
if ($this_is_home_page) {  
     $flag_disable_left = true;  
  }
```



### Turning off a column on EZ-Pages via Admin 
If you wish to disable left or right columns on specific EZ-Pages, go to 
Admin > Configuration > EZ-Pages Settings. 

To disable the left column on specific EZ-Pages, update the setting 
*EZ-Pages Pages to disable left-column*.

Simply list page ID numbers separated by commas with no spaces.  

Page ID numbers can be obtained from the EZ-Pages screen under Admin > Tools.  
ie: 21  
or leave blank.  

Here's another way to [modify sidebox display on EZ-Pages](/user/ezpages/sidebox_display_changes/).

### Other options: 
- To Globally disable the right column, go to [Admin > Configuration > Layout Settings](/user/admin_pages/configuration/configuration_layoutsettings/) and  set *Column Right Status - Global* to 0.
- There are also other ways to [change sidebox display](/user/sideboxes/suppressing_sidebox_display/).

