---
title: I don't have the file XXXXX in my template
description: Zen Cart Templated File missing 
category: new_user_topics
weight: 10
---

You're reading the instructions for a mod or a FAQ page or a forum post
and it says, 

```
Just update includes/templates/YOURTEMPLATE/templates/tpl_product_info_display.php ... 
```

and you say, "Wait a minute ... that file doesn't exist in my cart!" 

First of all, let's review two things: 

a) The FAQ [basic terms](/user/first_steps/basic_terms/) explains what YOURTEMPLATE means. 

b) The FAQ [template overrides system](/user/template/template_overrides/) explains what template overrides are.


So now you know `YOURTEMPLATE` is an alias for the name of your template,
and you know that template override files are files that are modified 
to create a custom look for your store. 

So if your template is `responsive_sheffield_blue`, this file would be 
`includes/templates/responsive_sheffield_blue/templates/tpl_product_info_display.php`. 

If you are using the built in default `responsive_classic` template, 
this file would be `includes/templates/responsive_classic/templates/tpl_product_info_display.php`. 

But what if the file still doesn't exist, even if you now know the real 
name of the file? 

Template files (the ones with `YOURTEMPLATE` - or some other [template indicator](/user/first_steps/basic_terms/#yourtemplate) in their name) are all
altered copies of the files in one directory above. 

So the file 

    includes/modules/responsive_sheffield_blue/additional_images.php

is a template modification file based on 

    includes/modules/additional_images.php

Likewise, the file 

    includes/languages/responsive_classic/english.php
is a template modification of 

    includes/languages/english.php

If the templated file being referenced doesn't exist in your cart, you can 
just create it by copying the original from one directory up. 

