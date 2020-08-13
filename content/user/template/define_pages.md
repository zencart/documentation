---
title: Define Pages 
description: Customizing your store with define pages 
category: templates
weight: 10
---

Define pages are special pieces of content that appear above normal page content for certain pages.  Unlike language strings, Define pages may be modified in the Admin.  The [Admin > Tools > Define Pages Editor](/user/admin_pages/tools/define_pages) help page lists the pages with define page content. 

The Define pages also come with a set of controls in admin, which are shown on [Admin > Configuration > Define Pages Status](/user/admin_pages/configuration/configuration_definepagestatus).  These controls allow you to determine whether the blog of content created by the Define Pages editor is shown on the associated page, and whether links to the associated page will be created. 

- The setting _Link ON_ means a link to the page will be created in any content block which is designed to link to this page.  For example, setting _Link ON_ for Define Page 2 means a link to `index.php?main_page=page_2` will be created in the Responsive Classic Mobile Menu, the More Information Sidebox and the Site Map.  Conversely, _Link OFF_ means no such link will be created. 

- The setting _Define Text ON_ means the text created in the [Define Pages Editor](/user/admin_pages/tools/define_pages/) will be displayed on the page in question.  For example, setting _Define Text ON_ for Define Main Page Status means the text created in `define_main_page.php` in the Define Pages Editor will be displayed on the home page. Conversely, _Define Text OFF_ for this page means the text will not be displayed.

As noted above, _Define Text ON_ always behaves the same way - it simply enables or disables the display of the block of text associated with it.  _Link ON_ is different - the interpretation of _Link ON_ is done as follows: 

<table>
<tr><th>Status Flag Name</th><th>Action</th></tr>
<tr><td>Define Main Page Status</td><td>None<td></td></tr>
<tr><td>Define Contact Us Status</td><td>Link to Contact Us page created in Site Map, Information Sidebox and Responsive Classic Mobile Menu<td></td></tr>
<tr><td>Define Privacy Status</td><td>Link to Privacy page created in Site Map and Responsive Classic Mobile Menu</td></tr>
<tr><td>Define Shipping & Returns</td><td>Link to Shipping Information page created in Site Map, Information Sidebox and Responsive Classic Mobile Menu</td></tr>
<tr><td>Define Conditions of Use</td><td>Link to Conditions of Use page created in Site Map, Information Sidebox and Responsive Classic Mobile Menu</td></tr>
<tr><td>Define Checkout Success</td><td>None</td></tr>
<tr><td>Define Discount Coupon</td><td>Link to Discount Coupon page created in Information Sidebox and Responsive Classic Mobile Menu</td></tr>
<tr><td>Define Site Map Status</td><td>Link to Site Map created in Site Map, Information Sidebox and Responsive Classic Mobile Menu</td></tr>
<tr><td>Define Page-Not-Found Status</td><td>None</td></tr>
<tr><td>Define Page 2</td><td>Link to Page 2 created in Site Map, More Information Sidebox and Responsive Classic Mobile Menu</td></tr>
<tr><td>Define Page 3</td><td>Link to Page 3 created in Site Map, More Information Sidebox and Responsive Classic Mobile Menu</td></tr>
<tr><td>Define Page 4</td><td>Link to Page 4 created in Site Map, More Information Sidebox and Responsive Classic Mobile Menu</td></tr>
</table>

_Link ON_ is also interpreted by some popular plugins such as Flexible Footer. 

If your needs go beyond what is provided by the define pages, take a look at the FAQ on [adding pages](/user/customizing/add_pages), which describes the use of [EZ-Pages](/user/ezpages/) as well as using plugins to build custom pages for your Zen Cart installation. 
