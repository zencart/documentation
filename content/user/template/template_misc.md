---
title: Miscellaneous Template Questions 
description: Miscellaneous Questions about Templates in Zen Cart
category: templates
weight: -2
---

Before you read this article, please be sure you are familiar with 
[Basic Terms](/user/first_steps/basic_terms/) used in describing
Zen Cart files. 

---

{{< misc >}} 

--- 

### How do I find the value of a configuration setting? 

If you're modifying a template and you want to check a config value, you can 
look at the [All Configuration Settings](/user/admin_pages/configuration/all/) page 
and do a search for the configuration title.  The configuration key will be 
shown when you find it, and you can use that in your code.  The configuration
key is created as a defined constant as part of the initialization code. 

Example: You want to display the value of the email address that emails
are sent from.  

Go to the page linked above, and search for `sent FROM`.  You'll see that the 
configuration key is `EMAIL_FROM`.   It's a defined constant so it doesn't 
need a `$`. 

```
<?php
echo "We welcome your feedback - just email " . EMAIL_FROM . ".<br />"; 
```

Conversely, if you're modifying a template, you might see a config like 
`SHOW_TOTALS_IN_CART`.
If you want to know where it is set, 
look at the [All Configuration Settings](/user/admin_pages/configuration/all/) page, 
and search for it. 
When you see it, look back up to the last header, you'll see it's in 
`Configuration > Layout Settings`, so now you know where it is set.


---

### What's the difference between templates and overrides? 
Creating a new template means you are using the 
[overrides](/user/first_steps/overrides/) system, 
even if just to create `includes/templates/YOURTEMPLATE` and 
folders below that.   But generally, a new template also uses 
more overrides: 

- language file overrides like `includes/languages/YOURTEMPLATE` and 
`includes/languages/english/YOURTEMPLATE` 
- code overrides like `/includes/modules/YOURTEMPLATE`

---
### What can I not override?
See [the list of non-overridable files](/user/template/template_overrides/#what-can-i-not-override).

---
### What is template default? 
See [the template default FAQ](/user/template/template_default/). 

---
### I created a new template, but can't see it in Admin > Tools > Template Selection

This can happen if you have forgotten to create the `template_info.php` file. 
See [the template_info FAQ](/user/template/template_info/). 

---

### Why does this mod not work with Template Monster Templates?
Zen Cart mods often depend on built-in Zen Cart features, which are 
removed as an expedient by Template Monster developers.  
If you're using a Template Monster template and a change you are 
trying isn't working, you'll need to figure out the difference 
between the relevant default files and the files that your template 
is using, and restore the missing features.

<br /><br />


---
<!-- please keep this at the end --> 
{{< faq_questions >}}
