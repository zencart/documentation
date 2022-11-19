---
title: Switching templates 
description: Changing configuration values when template changes 
category: template
weight: 10
---

The process of changing templates can be done using the [Template Selection](/user/admin_pages/tools/template_selection/) screen under Admin > Tools. 

But what if the templates you are switching between expect different configuration values?  It's tedious to do these by hand, especially if you're switching back and forth doing tests.

That's why Zen Cart 1.5.8a introduces a new feature called `template_init`.  Place a file called `template_init.php` in the includes/templates/YOURTEMPLATE folder.  It will run when the template  is set to YOURTEMPLATE.

For example, here's a template init that turns off CSS buttons when this template is selected: 

```
<?php
// Settings for Older Template
$db->Execute("UPDATE " . TABLE_CONFIGURATION . " SET configuration_value='No' WHERE configuration_key  = 'IMAGE_USE_CSS_BUTTONS'");
```
Any configuration variable can be set in the same way.

If you can't recall the name of a particular variable, remember you can look it up on the  [All Configuration Settings](/user/admin_pages/configuration/all/) page. 

If you are using an older Zen Cart version and want this feature, you can merge [this PR](https://github.com/zencart/zencart/pull/5370/files) into your copy of `admin/template_select.php`.
