---
title: Template Images 
description: What directories contain all the template images, buttons, and icons? 
category: template
weight: 10
---

Note that by default, YOURLANGUAGE is "english" and YOURTEMPLATE is "responsive_classic". 

`images` folder: This is where your Product images are located.

`includes/languages/YOURLANGUAGE/images` folder: icon.gif (your language flag).

`includes/templates/YOURTEMPLATE/buttons/YOURLANGUAGE` folder: contains the buttons used by the cart, if you are not using [CSS buttons](/user/template/buttons/).

`includes/templates/YOURTEMPLATE/images` folder: contains `logo.gif`, and other images required by your template files.

`includes/templates/YOURTEMPLATE/images/icons` folder: contains additional images used by the cart (specific to your template)

**NOTE:** if your template is looking for an image in the 
`includes/templates/YOURTEMPLATE/images` folder but cannot find it, Zen Cart will use the image in the `includes/templates/template_default/images` folder.

**NOTE:** if you update your `logo.gif` filename or filename extension or the dimensions of the image, you need to also make corresponding adjustments to your `header.php` file as described at: https://docs.zen-cart.com/user/new_user_topics/change_header_logo.

