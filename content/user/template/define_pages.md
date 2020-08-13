---
title: Define Pages 
description: Customizing your store with define pages 
category: templates
weight: 10
---

Define pages are special pieces of content that appear above normal page content for certain pages.  Unlike language strings, Define pages may be modified in the Admin.  The [Admin > Tools > Define Pages Editor](/user/admin_pages/tools/define_pages) help page lists the pages with define page content. 

Using the admin, it is also possible to [change the status of define pages](/user/admin_pages/configuration/configuration_definepagestatus) as follows: 

- The setting Link ON means a link to the page will be created in any content block which is designed to link to this page.  For example, setting Link ON for Define Page 2 means a link to `index.php?main_page=page_2` will be created in the Responsive Classic Mobile Menu, the More Information Sidebox and the Site Map.  Conversely, Link OFF means no such link will be created. 

- The setting Define Text ON means the text created in the [Define Pages Editor](/user/admin_pages/tools/define_pages/) will be displayed on the page in question.  For example, setting Define Text ON for Define Main Page Status means the text created in `define_main_page.php` in the Define Pages Editor will be displayed on the home page. 

If your needs go beyond what is provided by the define pages, take a look at the FAQ on [adding pages](/user/customizing/add_pages), which describes the use of [EZ-Pages](/user/ezpages/) as well as using plugins to build completely custom pages containing PHP code. 
