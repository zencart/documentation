---
title: Adding Pages to my site 
description: Creating a new page for your store
category: customizing 
weight: 10
---

You have several options if you want to add a page to your site.  Here they are, in increasing order of complexity: 

### Use EZ-Pages

[EZ-Pages](/user/ezpages/what_are_ezpages/) are a great way to add new text content to your site. 
The one restriction they have is that you can't execute any PHP code on them,
but for many situations, this is not required.

### Use the built-in extra pages

The built-in [extra pages](/user/template/extra_pages) are 

- [page_2](/user/admin_pages/configuration/configuration_definepagestatus/#define_page_2) 
- [page_3](/user/admin_pages/configuration/configuration_definepagestatus/#define_page_3) 
- [page_4](/user/admin_pages/configuration/configuration_definepagestatus/#define_page_4)

You may use these pages to add content to your site. 

Turn on creation of links to these pages from [Admin > Configuration > Define Page Status](/user/admin_pages/configuration/configuration_definepagestatus/), then modify the page content using the [Define Pages Editor](/user/admin_pages/tools/define_pages/). 

### Use a Plugin 

This plugin adds six new define pages which can be used just like page_2 .. page_4.

- [Twitch Add Extra Pages - Add Define Pages](https://www.zen-cart.com/downloads.php?do=file&id=2319) 

### Build a new custom page 

A number of files go into building a new page.  The best way to create a new page is to use one of these plugins as a starting point: 

- [About Us](https://www.zen-cart.com/downloads.php?do=file&id=86) 

- [Skinny About Us](https://www.zen-cart.com/downloads.php?do=file&id=2198) 

The latter is somewhat less customizable but contains fewer files. 

(Note that the About Us page is built in to Zen Cart 1.5.8 and higher; these plugins are referenced only as examples of how to build a page.) 

The advantage of creating a new page is that you can use PHP in the page, which is not an option with EZ-Pages.  Being able to use PHP means you can add conditional logic, do database lookups, customize for specific groups or customer characteristics, etc. 

### Add infrastructure to build multiple pages 

Use this plugin as a starting point: 
- [News Box Manager](https://www.zen-cart.com/downloads.php?do=file&id=2264) 


## Linking to your New Page 

Once you have created your new page, you'll want to link to it. A few options are: 

- If you have created the page as an EZ-Page, use the [EZ-Pages sidebox](/user/sideboxes/ezpages_sidebox/).  
- If you want the link in the Information Sidebox, use the instructions on [adding a link to the Information Sidebox](/user/sideboxes/add_link_information_sidebox/).  
- You can put the link in the [header](/user/template/header/) or [footer](/user/template/footer/) of your site, but the method of doing so will depend on your template.

## Direct Access to Files 

You may wish to simply provide files (such as PDFs) on your site without requiring the registration and purchase steps associated with paid downloads.

The recommended method of doing this is as follows:

- Create a new folder at the top level of your cart.  Remember that Zen Cart already comes with `/docs` and `/download` folders, so choose another name. 
- Prior to populating the folder, create an `index.html` and `.htaccess` file that limits access in the folder.  You can copy these files from the `/download` folder and customize as needed.  
Note: If you are using Ngnix or another webserver other than Apache, you will have to make the appropriate security changes for that system. 

If what you want to do is associate PDFs with specific products, look at the [PDF Attachment in Product Description](https://www.zen-cart.com/downloads.php?do=file&id=1642) plugin.

