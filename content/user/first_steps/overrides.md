---
title: Basics - default files, template default and overrides 
description: Default Files, Override Files and Templates in Zen Cart Basic 
category: first_steps 
weight: 10
---

Zen Cart has a templating capability that allows you to modify the 
functionality and appearance of the cart.  When done properly, you 
can "revert" to original behavior and appearance for troubleshooting. 

When you first install Zen Cart, the template which is in use is called
`responsive_classic`.  This is a new template, introduced in Zen Cart 1.5.5,
which works on both desktop computers and mobile devices. 

The files which determine how the page will be displayed are called 
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
the *default file* (or *base file*) instead. 

### Default Files 

How do you find the default file? 

There are two possibilities: 

a) For files under `/includes/templates`, the default file is `includes/templates/template_default/FOLDER/FILENAME`. 

So the file 

    includes/templates/responsive_sheffield_blue/templates/tpl_product_info_display.php

is a template modification file based on 

    includes/templates/template_default/templates/tpl_product_info_display.php

This is the [default template](/user/template/template_default). 


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
create it by copying the original from the default file. 

Ready to read more about overrides? [Go here](/user/new_user_topics/overrides).

