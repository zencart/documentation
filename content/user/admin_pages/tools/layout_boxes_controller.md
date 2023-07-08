---
title: Layout Boxes Controller
category: admin_pages
weight: 10
---

This page allows you to select which [sideboxes](/user/template/sideboxes/) are shown 
on your storefront, and where they should be placed.  

This page changed significantly in Zen Cart 1.5.8 due to 
the introduction of the `$uses_single_column_layout_settings` entry in the [template_info](/user/template/template_info/) file. 

For templates that have `$uses_single_column_layout_settings` set to true  
![layout Boxes Controller Single](/images/layout_boxes_controller_single.png)

Editing an an entry will bring up a dialog like this:  
![Layout Boxes Controller Edit Single](/images/layout_boxes_controller_edit_single.png)

For templates that have `$uses_single_column_layout_settings` set to false  
![Layout Boxes Controller](/images/layout_boxes_controller.png)

Editing an an entry will bring up a dialog like this:   
![Layout Boxes Controller Edit](/images/layout_boxes_controller_edit.png)

### Sideboxes 

There are many [built-in sideboxes](/user/sideboxes/sidebox_list/).  Choose the ones that would be most beneficial for your store.  You can also [design your own sidebox](/user/sideboxes/build_sidebox/) if what you need is not already available. 

For more information about sideboxes, see [the sidebox FAQs](/user/sideboxes/).

### Copying Sidebox Settings 

After moving to a new template, the initial sidebox settings will likely be all off.  In 1.5.8 and above, you may copy the sidebox settings from another template easily using the Reset Settings tool.

![Reset Settings](/images/reset_settings.png)

The reset settings tool only shows templates which exist under `includes/templates/`, so if you're doing an upgrade and switching templates, and you don't want to copy in the old template, you should use the [Copy Sideboxes](https://www.zen-cart.com/downloads.php?do=file&id=1828) plugin.

Users of releases prior to 1.5.8 should also use the [Copy Sideboxes](https://www.zen-cart.com/downloads.php?do=file&id=1828) plugin to copy sidebox settings.


### Layout Boxes Controller prior to 1.5.8

Here is a picture of screen prior to 1.5.8: 

![Old Layout Boxes Controller](/images/layout_boxes_controller_old.png) 

The Edit screen was also different: 

![Layout Boxes Controller Edit](/images/layout_boxes_controller_edit_old.png)

