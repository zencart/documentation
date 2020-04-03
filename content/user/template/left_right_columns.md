---
title: Left and Right Columns - turning them off 
description: Left and Right Columns in Zen Cart - turning them off 
category: templates
weight: 10
---

Firstly, if you don't already have one, create an over-ride file for tpl_main_page.php in your `includes/templates/YOURTEMPLATE/common` directory.  

There is enormous scope within this one module to create turn the left and right hand columns on and off according to which page or category is to be displayed. Open it up and you will see a large comment at the top explaining some of them. Here are a few examples to help illustrate that.

If you wish to turn off the left hand column for the "contact us" and "terms & conditions" pages, find the following block of code  

```
if (in_array($current_page_base,explode(",",'list_pages_to_skip_all_right_sideboxes _on_here,separated_by_commas,and_no_spaces')) ) {  
     $flag_disable_right = true;  
  }
```

and edit it to read  

```
if (in_array($current_page_base,explode(",",**'contact_us,conditions'**)) ) {  
     $flag_disable_**left** = true;  
  }
```

If you wished to disable both columns in category listings either add or edit the above block to read  
```
if (in_array($cPath,explode(",",'3,8')) ) {  
    $flag_disable_right = true;  
    $flag_disable_left = true;  
  }
```

To disable the right column for a series of EZ-Pages  
```
if (in_array($ezpage_id,explode(",",'2,5'))) {  
    $flag_disable_right = true;  
  }
```

Or, you can use the settings in Admin > Configuration > EZ-Pages Settings:  
For example:  

**EZ-Pages Pages to disable left-column**  

EZ-Pages "pages" on which to NOT display the normal "left" column (of sideboxes) for your site.  
Simply list page ID numbers separated by commas with no spaces.  
Page ID numbers can be obtained from the EZ-Pages screen under Admin > Tools.  
ie: 21  
or leave blank.  

[Here's another way to do this](/user/ezpages/sidebox_display_changes/).

To turn off the left column for the home page only, you would insert the following:  

```
if ($this_is_home_page) {  
     $flag_disable_left = true;  
  }
```
