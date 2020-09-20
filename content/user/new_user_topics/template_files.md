---
title: Template Files - What are they and how are they used?
description: What does a template do? 
category: new_user_topics
weight: 10
---

The template files used in Zen Cart provide the structure and layout of the various pages of your cart. They make use of the definitions from your [language files](/user/new_user_topics/language_files/). 

These files are located in `includes/templates/template_default`.
Template files are of three types; common, specific pages and sideboxes. 
The files can be identified by
a `tpl` prefix (e.g. `tpl_shopping_cart_default.php`)
These files contain all the information necessary to construct the pages used by your shop.

Common Template Files are located in 
`includes/templates/template_default/common`.
These files are "common" to every page used throughout Zen Cart.
These files consist of the Main Page, the Header, the Footer and the Box files used for the sideboxes.

Page Specific Template Files are located in 
`includes/templates/template_default/templates`.
These files represent the pages of your cart and include the Index page, the Log in page and the Product Display pages.

You can change the layout of each page in your shop by editing these 
page-specific template files. 

Sidebox Template Files are located in
`includes/templates/template_default/sideboxes`.

These files contain the instructions for placing content into the sideboxes you are using.

