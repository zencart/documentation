---
title: Creating the template_info.php file
description: Why doesn't my template show up in Tools > Template Selection? 
category: template
weight: 10
---

Activating your template so that you can use your overrides files 
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
```

Notice there is no closing PHP tag.  

Create a screenshot of your template, and save it as `includes/templates/YOURTEMPLATE/images/screenshot.jpg`.  This way people will be able to "preview" your template.  


