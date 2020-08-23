---
title: Creating your own Template 
description: The steps required to build a Zen Cart template 
category: template 
weight: 10
aliases: 
   - /user/template/customizing
---

To get ideas about building your own template, take a look at the 
other templates available for Zen Cart. 

{{< templates >}}

<br><br>

This is an outline of the steps you should follow: 

1. make a new folder, perhaps something like `includes/templates/mary`.  This is the working area for your own custom template

1. make 4 subfolders in there:

    ```
    common/
    css/
    images/
    templates/
    ```

1. copy the existing files from the `responsive_classic/css` and `responsive_classic/images` into the appropriate folders in your new working area

1. copy `tpl_header.php` from the `responsive_classic/common` folder.  You'll want to edit this file to incorporate your custom page-header.  This file governs the appearance of the top of all of your pages.

1. copy `tpl_footer.php` from the `responsive_classic/common` folder.  You can edit the footer area to appear as you like.

1. While working on #4 and #5 above, you can also modify the `css/stylesheet.css` file in your working area, to set the styles for your template.  You can copy your existing stylesheet into the `css` folder, making sure it's named `stylesXXXXXXX.css` (ie: `styles_mine.css`). All files in this folder are loaded by your zen cart site in alphabetical order, and cascading rules will determine the combination of effects in that order.

1. The colors for the main area of your site and the sideboxes, etc can be controlled in the stylesheet.

1. If you need a very different page-layout from the default, you can copy `tpl_main_page.php` from the `responsive_classic/common` folder to your `common` folder, and alter it.  This file builds your pages, starting with the header, then the left column of sideboxes, the middle "content" area of the site, then the right column of sideboxes, followed finally by the footer. Thus, by styling this page, you can control the appearance of the whole site. In many cases, you don't need to touch it though, as much of the control is in the stylesheet already.

1. Finally, create the `template_info.php` file in your working template folder. Instructions on creating this file and activating your template can be found in [the template_info FAQ](/user/template/template_info/). 

