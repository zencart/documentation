---
title: Basics - Default files, template default and overrides 
description: What is a default file vs a template file? 
category: first_steps 
weight: 10
---

Zen Cart has a templating capability that allows you to modify the 
functionality and appearance of the cart.  This capability sometimes called 
"overrides," "template overrides," or "overriding a file."  

Once you have built a new template (more on this later) and overridden
the files you want to change, you can switch back and forth between
your new template and the default template from the admin using 
[Tools > Template Selection](/user/admin_pages/tools/template_selection/).
Thus, the advantage of using overrides versus modifying the original files directly
is that with overrides, you can "revert" to original behavior and appearance 
quickly and easily for troubleshooting. 

When you first install Zen Cart, the template which is in use is called
`responsive_classic`.  This is a new template, introduced in Zen Cart 1.5.5,
which works on both desktop computers and mobile devices. 

### Template Files 

The files which determine how the page will appear are called 
*template files*.  In the case of `responsive_classic`, they can be 
found in the following folders: 

```
./templates/responsive_classic
./modules/responsive_classic
./languages/english/extra_definitions/responsive_classic
./languages/english/responsive_classic
./languages/english/html_includes/responsive_classic
```

The files under these folders are called `overrides`.  In other words, Zen Cart's basic functionality and appearance has been `overridden` by these files. 

Some files *could* be overridden but are currently not - for example, 
the site map template file (`tpl_site_map_default.php`) is not part of 
the `responsive_classic` template.  When this happens, Zen Cart uses 
the *default file* instead. 

**Note:** Sometimes the default file is called the *base file* or the *core file* instead. These terms are all interchangeable. 

### Default Files 

How do you find the default file? 

There are two possibilities: 

a) For files under `/includes/templates`, the default file is `includes/templates/template_default/FOLDER/FILENAME`. 

So the file 

    includes/templates/responsive_sheffield_blue/templates/tpl_product_info_display.php

is a template modification file based on 

    includes/templates/template_default/templates/tpl_product_info_display.php

This is the [default template](/user/template/template_default/). 


b) For all other files, the default file is one level above the template folder. 

So the file 

    includes/modules/responsive_sheffield_blue/additional_images.php

is a template modification file based on 

    includes/modules/additional_images.php

Likewise, the file 

    includes/languages/responsive_classic/english.php
is a template modification of 

    includes/languages/english.php

If a templated file doesn't exist in your cart, you can 
create it by simply copying the default file.  See the [I don't have the file ...](/user/new_user_topics/no_such_file/) FAQ for more detail. 

And remember: if you aren't changing a file, there is *no need* to copy it 
from the default file - the default file will be used by Zen Cart
automatically.  For this reason, you should expect your template to have
many fewer files than the default template.  

When you're ready, you can [read more about overrides](/user/new_user_topics/overrides/).

