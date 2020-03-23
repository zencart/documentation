---
title: Customizing a Template 
description: Customizing a Template in Zen Cart 
category: template 
weight: 10
---

1. make a new folder, perhaps something like:

includes/templates/mary

This is the working area for your own custom template

2. make 4 subfolders in there:

- common

- css

- images

- templates


3. copy the existing files from the template_default/css and template_default/images into the appropriate folders in your new working area

4. copy the "tpl_header.php" from the template_default/common folder

You'll want to edit this file to incorporate your custom page-header. This is the appearance of the tops of all your pages.

5. copy the "tpl_footer.php" from the template_default/common folder

You can edit the footer area to appear as you like.

6. While working on #4 and #5 above, you can also meddle in the css/stylesheet.css file in your working area, to set the styles for your template.

You can copy your existing stylesheet into the css folder, making sure it's named stylesXXXXXXX.css (ie: styles_mine.css). All files in this folder are loaded by your zen cart site in alphabetical order...and inheritance rules will determine the combination of effects in that order.


7. The colors for the main area of your site and the sideboxes, etc can be controlled in the stylesheet.

8. If you need a very different page-layout from the default, you can copy the "tpl_main_page.php" file from the template_default/common folder to your common folder, and alter it.

This file assimilates everything, starting with the header, then the left column of sideboxes, the middle "content" area of the site, then the right column of sideboxes, followed finally by the footer. Thus, if you style this page strategically, you can control the whole site. In many cases, you don't need to touch it though, as much of the control is in the stylesheet already.

9. Copy the template_default/template_info.php to your working template folder and update its name. Instructions on this and on activating your new template and sideboxes can be found here.
