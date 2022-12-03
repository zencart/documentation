---
title: Creating the template_info.php file
description: Why doesn't my template show up in Tools > Template Selection? 
category: template
weight: 10
---

Activating your template so that you can use your [overrides](/user/template/template_overrides/)
requires two final steps (the first is one time only, of course). 

a. Create `includes/templates/YOURTEMPLATE/template_info.php`

In order for the system to "see" your template, the `template_info.php`
file must exist inside the `includes/templates/YOURTEMPLATE` folder. 

Create it as follows: 

```
<?php 
$template_name = 'Your Template Name'
``` 

b. Login to your Admin panel and go to [Tools > Template Selection](/user/admin_pages/tools/template_selection/).  You should see your new custom template(s) in the dropdown list. Select your template.

You are now using your new template. 

### Full specification for template_info file 

If you are going to distribute your template, you should build out the
`template_info.php` file more completely.  Use this 

```
<?php  
$template_name = 'YOURTEMPLATE';  
$template_version = 'Version 1.0';  
$template_author = '<enter your name>';  
$template_description = 'describe your template'; 
$template_screenshot = 'screenshot.jpg';  
$uses_single_column_layout_settings = (isset($uses_single_column_layout_settings)) ? $uses_single_column_layout_settings : true;
```

Create a screenshot of your template, and save it as `includes/templates/YOURTEMPLATE/images/screenshot.jpg`.  This way people will be able to "preview" your template.  

The `$uses_single_column_layout_settings` entry is new to Zen Cart 1.5.8a and forward. (PR for Zen Cart 1.5.8 users [here](https://github.com/zencart/zencart/pull/5429)).  It indicates whether or not the Admin [Layout Boxes Controller](/user/admin_pages/tools/layout_boxes_controller/) displays the 'SINGLE COLUMN' sort-order and status fields. Your template's default (either true or false) indicates whether the template itself includes sideboxes (like those which reside in the header) that check for the `layout_box_single_sort_order` and/or `layout_box_single_status` in determining whether or not their content is displayed. It's a good idea (as in the example above) to check to see if the variable already exists, in case a store needs to further control these settings.

Notice there is no closing PHP tag.  

