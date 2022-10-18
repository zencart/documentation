---
title: Define Pages 
description: Customizing your store with define pages 
category: template
weight: 10
---

Define pages are special pieces of content that appear above normal page content for certain pages.  Unlike language strings, Define pages may be modified in the Admin.  The [Admin > Tools > Define Pages Editor](/user/admin_pages/tools/define_pages/) help page lists the pages with define page content. 

The phrase "Define Pages" can also be used to refer to the stand-alone pages whose content is created in the Define Pages Editor, and which are controlled using the [Define Pages Status](/user/admin_pages/configuration/configuration_definepagestatus/) admin page.

The Define pages also come with a set of controls in admin, which are shown on [Admin > Configuration > Define Pages Status](/user/admin_pages/configuration/configuration_definepagestatus/).  These controls allow you to determine whether the block of content created by the Define Pages editor is shown on the associated page, and whether links to the associated page will be created. 

- The setting _Link ON_ means a link to the page will be created in any content block which is designed to link to this page.  For example, setting _Link ON_ for Define Page 2 means a link to `index.php?main_page=page_2` will be created in the Responsive Classic Mobile Menu, the More Information Sidebox and the Site Map.  Conversely, _Link OFF_ means no such link will be created. 

- The setting _Define Text ON_ means the text created in the [Define Pages Editor](/user/admin_pages/tools/define_pages/) will be displayed on the page in question.  For example, setting _Define Text ON_ for Define Main Page Status means the text created in `define_main_page.php` in the Define Pages Editor will be displayed on the home page. Conversely, _Define Text OFF_ for this page means the text will not be displayed.

As noted above, _Define Text ON_ always behaves the same way - it simply enables or disables the display of the block of text associated with it.  _Link ON_ is different: it controls the creation of links to the associated page.  The interpretation of _Link ON_ is done as follows: 

<br>

Status Flag Name | Behavior if Link ON 
-----------------|-------
Define Main Page Status | None
Define Contact Us Status | Link to Contact Us page created in Site Map, Information Sidebox and Responsive Classic Mobile Menu
Define Privacy Status | Link to Privacy page created in Site Map and Responsive Classic Mobile Menu
Define Shipping & Returns | Link to Shipping Information page created in Site Map, Information Sidebox and Responsive Classic Mobile Menu
Define Conditions of Use | Link to Conditions of Use page created in Site Map, Information Sidebox and Responsive Classic Mobile Menu
Define Checkout Success | None
Define Discount Coupon | Link to Discount Coupon page created in Information Sidebox and Responsive Classic Mobile Menu
Define Site Map Status | Link to Site Map created in Site Map, Information Sidebox and Responsive Classic Mobile Menu
Define Page-Not-Found Status | None
Define Page 2 | Link to Page 2 created in Site Map, More Information Sidebox and Responsive Classic Mobile Menu
Define Page 3 | Link to Page 3 created in Site Map, More Information Sidebox and Responsive Classic Mobile Menu
Define Page 4 | Link to Page 4 created in Site Map, More Information Sidebox and Responsive Classic Mobile Menu

<br>

_Link ON_ is also interpreted by some popular plugins such as Flexible Footer. 

<br>
<div id="define_page_files"></div>

The pages listed below are considered Define Pages, since their content is controlled using the Define Pages Editor.

<br>

Page Name | File| URL 
----------|-----|-----
About Us| `define_about_us.php` | `index.php?main_page=about_us` (1.5.8 andabove)
Ask a Question | `define_ask_a_question.php` | `index.php?main_page=ask_a_question`  (1.5.7 and above)
Contact Us | `define_contact_us.php` | `index.php?main_page=contact_us` 
Privacy | `define_privacy.php` | `index.php?main_page=privacy`  
Shipping Info | `define_shippinginfo.php` | `index.php?main_page=shippinginfo` 
Conditions of Use | `define_conditions.php` | `index.php?main_page=conditions` 
Discount Coupon | `define_discount_coupon.php` | `index.php?main_page=coupons` 
Site Map  | `define_site_map.php` | `index.php?main_page=site_map`  
Page 2 |  `define_page_2.php` | `index.php?main_page=page_2`
Page 3 |  `define_page_3.php` | `index.php?main_page=page_3` 
Page 4 | `define_page_4.php` | `index.php?main_page=page_4`  

<br>

These pages have other content, and define page content is embedded along side that: 


Page Name |  File | URL 
----------|-------|-----
Shopping Cart |`define_shopping_cart.php` |  `index.php?main_page=shopping_cart`
Checkout Success |`define_checkout_success.php` |  `index.php?main_page=checkout_success`
Home Page |`define_main_page.php` |  `index.php`

Some newer pages use the [site specific overrides](/user/customizing/site_specific_overrides/) file for enabling/disabling links instead of Configuration > Define Pages: 

- About Us 
- Brands 

If your needs go beyond what is provided by the define pages, take a look at the FAQ on [adding pages](/user/customizing/add_pages/), which describes the use of [EZ-Pages](/user/ezpages/) as well as using plugins to build custom pages for your Zen Cart installation. 

### Related 

- [ Why does my define page not show up in Define Pages Editor?](/user/troubleshooting/define_not_showing/)
- [ Extra Pages](/user/template/extra_pages/)

