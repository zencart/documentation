---
title: Site Header  
description: How can I change my storefront header layout? 
category: template
weight: 10
---

The storefront header is content that will appear at the top of every page. 
It includes your logo, tagline text (if any) and possibly menus and links.

![Header](/images/header.png) 

<br>

The links in the black background are created by `includes/templates/YOURTEMPLATE/common/tpl_header.php`. 

The search box in the upper right is called [header search](/user/sideboxes/search_box_header_only/).

Below this is the logo and tagline.  Both of these are set in `includes/languages/english/YOURTEMPLATE/lang.header.php`  (or `includes/languages/english/YOURTEMPLATE/header.php` for 1.5.7 and below).

The block of links with the blue background is called [categories tabs](/user/new_user_topics/categories_tabs/). 

The block of links below them with the gray background is called the [EZ-Pages Header Bar](/user/ezpages/ezpages_header_bar/).

Once a customer has logged in, more menu items appear on the black bar. 

![Header after Login](/images/logged_in_header.png) 

On a mobile device, these menu items are provided by icons. 

![Mobile Header closed](/images/mobile_closed.png)

Clicking on the hamburger icon on the left opens up a menu with text links 

![Mobile Header open](/images/mobile_open_logged_in.png)

Notice that additional links are also provided.  These are created in `includes/templates/responsive_classic/templates/tpl_modules_mobile_menu.php`.

### Related Links: 

- [How do I change the header logo?](/user/new_user_topics/change_header_logo/)
- [How do I change the header background?](/user/new_user_topics/change_header_image/)

