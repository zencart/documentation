---
title: Switching templates 
description: Changing configuration values when template changes 
category: template
weight: 10
---

**Note:** Users of Zen Cart 2.0.0 and above have access to the even more powerful [template settings](/dev/code/template_settings/) file feature. 

The process of changing templates can be done using the [Template Selection](/user/admin_pages/tools/template_selection/) screen under Admin > Tools. 

But what if the templates you are switching between expect different configuration values?  It's tedious to do these by hand, especially if you're switching back and forth doing tests.

That's why Zen Cart 1.5.8a introduced a new feature called Template Init.  Here's how it works:

- Place a file called `template_init.php` in the includes/templates/YOURTEMPLATE folder.  
- The file will run when the template is set to YOURTEMPLATE from Admin > Tools > Template Selection.

Note this feature is not available when using  [Private Template Testing](/user/template/private_testing/).

For example, here's a `template_init.php` file that turns off CSS buttons when this template is selected: 

```
<?php
// Settings for Older Template
$db->Execute("UPDATE " . TABLE_CONFIGURATION . " SET configuration_value='No' WHERE configuration_key = 'IMAGE_USE_CSS_BUTTONS'");
```

A corresponding query should exist in `template_init.php` of the other template(s) to restore the value when switching back:

```
<?php
// Settings for Newer Template(s)
$db->Execute("UPDATE " . TABLE_CONFIGURATION . " SET configuration_value='Yes' WHERE configuration_key = 'IMAGE_USE_CSS_BUTTONS'");
```

Any configuration variable can be set in the same way.

If you can't recall the name of a particular variable, remember you can look it up on the  [All Configuration Settings](/user/admin_pages/configuration/all/) page. 

If you are using an older Zen Cart version and want this feature, you can merge [this PR](https://github.com/zencart/zencart/pull/5370/files) into your copy of `admin/template_select.php`.

This capability makes it easy to switch back and forth between the [Bootstrap](/user/template/bootstrap/) and [Responsive Classic](/user/template/responsive_classic/) templates.  

Create `includes/templates/bootstrap/template_init.php` as follows:
```
<?php
// Settings for Bootstrap
$db->Execute("UPDATE " . TABLE_CONFIGURATION . " SET configuration_value='0' WHERE configuration_key = 'PRODUCT_LISTING_COLUMNS_PER_ROW'");
```

Then  create `includes/templates/responsive_classic/template_init.php` as follows: 

```
<?php
// Settings for Responsive Classic
$db->Execute("UPDATE " . TABLE_CONFIGURATION . " SET configuration_value='1' WHERE configuration_key = 'PRODUCT_LISTING_COLUMNS_PER_ROW'");
```

Now switching to Bootstrap will make your product listing pages display in [fluid mode](/user/template/listing_columns/), and switching to Responsive Classic will make your product listing pages display in rows mode, without you having to remember to make admin changes.

