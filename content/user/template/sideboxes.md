---
title: Sideboxes 
description: What are Zen Cart sideboxes? 
category: template
weight: 10
---

Sideboxes are narrow pieces of content that are displayed on the left and right side of the screen in the Zen Cart storefront in a desktop view.  (The smaller width of a mobile screen means they are either hidden or put in the middle of the screen on such devices.)

You can learn about [controlling sideboxes in the admin](/user/admin/sideboxes/) so that you only display the sideboxes that are most important to your store. 

Zen Cart has a number of sideboxes that come pre-built. 
You can see all the available sideboxes in the [sidebox list](/user/sideboxes/sidebox_list/) FAQ. 

The Information Sidebox, for example, is just a list of links. 
The Specials Sidebox, on the other hand, shows product images and information. 

<br>
<div style="float: left;">
  <div style="float: left; margin-right: 10px;">
    <img alt="Information Sidebox" src="/images/information_sidebox.png" />
  </div>
  <div style="float: left;">
    <img alt="Specials Sidebox" src="/images/specials_sidebox.png" />
  </div>
</div>
<br clear="all">
<br>


### Sideboxes and Mobile 

[Responsive](/user/template/responsive/) templates often not display sideboxes on a mobile device (especially a phone) due to space limitations.  Instead the links provided by sideboxes may be accessed from the hamburger menu at the top of the site. 

<img alt="Mobile - closed" src="/images/mobile_closed.png" />

When you click on the hamburger icon at the top left, then menu opens 

<img alt="Mobile - open" src="/images/mobile_open.png" />

From there you can navigate to the desired page. 

This behavior is different from that of [centerboxes](/user/template/centerboxes/), which appear as normal on mobile. 

#### Controlling Sideboxes on Mobile Menu

If you wish to add more links to your mobile-menu sidebar beyond those which are controlled via Admin Switches, you may need to edit PHP files to add those links by hand.

In the case of the `responsive_classic` template the file to edit is `/includes/templates/YOURTEMPLATE/templates/tpl_modules_mobile_menu.php`


### Sidebox Controls 

The number of products shown in a sidebox is controlled using an Admin setting on the page [Admin > Configuration > Maximum Values](/user/admin_pages/configuration/configuration_maximumvalues/).  There are many such settings; here are a few: 

Sidebox Name | Control 
----------|------- 
Specials | Random Products On Special for SideBox
New Products | Random New Products for SideBox
Featured Products | Random Featured Products for SideBox

###  Creating your own sidebox 

In addition to the [built-in sideboxes](/user/sideboxes/sidebox_list/), other sideboxes are available in the [sideboxes section of the Zen Cart plugins library](https://www.zen-cart.com/downloads.php?do=cat&id=12).  For example, the [Blank Sidebox](https://www.zen-cart.com/downloads.php?do=file&id=80) allows you to create your own sidebox with whatever content you wish. 

### Controlling sidebox display 

On some pages, it may be desirable to disable some or all sideboxes.  See [Suppressing sidebox display on specific pages](/user/sideboxes/suppressing_sidebox_display/) for instructions on doing this.


