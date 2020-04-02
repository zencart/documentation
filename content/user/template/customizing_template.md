---
title: Customizing a Template 
description: Customizing a Template in Zen Cart 
category: template 
weight: 10
---

**Note:** For modern templates, which are expected to run on both 
desktop computers and mobile devices, `responsive_classic` is 
a better choice of a starting point.  However, if you are certain your 
template will be desktop only, you can use `template_default`.


1. make a new folder, perhaps something like:

`includes/templates/mary`

This is the working area for your own custom template

2. make 4 subfolders in there:

```
common/
css/
images/
templates/
```

3. copy the existing files from the `responsive_classic/css` and `responsive_classic/images` into the appropriate folders in your new working area

4. copy `tpl_header.php` from the `responsive_classic/common` folder

You'll want to edit this file to incorporate your custom page-header. 
This file governs the appearance of the top of all of your pages.

5. copy `tpl_footer.php` from the `responsive_classic/common` folder

You can edit the footer area to appear as you like.

6. While working on #4 and #5 above, you can also modify the `css/stylesheet.css` file in your working area, to set the styles for your template.

You can copy your existing stylesheet into the `css` folder, making sure it's named `stylesXXXXXXX.css` (ie: `styles_mine.css`). All files in this folder are loaded by your zen cart site in alphabetical order, and cascading rules will determine the combination of effects in that order.

7. The colors for the main area of your site and the sideboxes, etc can be controlled in the stylesheet.

8. If you need a very different page-layout from the default, you can copy `tpl_main_page.php` from the `responsive_classic/common` folder to your `common` folder, and alter it.

This file builds your pages, starting with the header, then the left column of sideboxes, the middle "content" area of the site, then the right column of sideboxes, followed finally by the footer. Thus, by styling this page, you can control the appearance of the whole site. In many cases, you don't need to touch it though, as much of the control is in the stylesheet already.

9. Finally, create the `template_info.php` file in your working template folder. Instructions on creating this file and activating your template can be found in
[this FAQ](/user/template/template_info/). 

