---
title: How do I change the logo or the logo alt text?
description: Changing the logo in Zen Cart 
category: new_user_topics
weight: 10
---

By default, Zen Cart uses `includes/templates/YOURTEMPLATE/images/logo.gif` 
for the name of the logo image, but you can use you own filename for the logo.

Using an [image editor](/user/first_steps/useful_tools/#graphics-editors), create your new logo and save it to `includes/templates/YOURTEMPLATE/images/yourname` and upload it to your server.

The name `yourname` will also include a file extension, such as `.png`, `.jpg`, etc. 

After creating your logo you can adjust the alt text, width, height, and image name in `includes/languages/english/YOURTEMPLATE/header.php`

```
define('HEADER_ALT_TEXT', 'Powered by Zen Cart :: The Art of E-Commerce');
define('HEADER_LOGO_WIDTH', '192px');
define('HEADER_LOGO_HEIGHT', '64px');
define('HEADER_LOGO_IMAGE', 'logo.gif');
```

Save this file and upload it to your server. 

By default, the logo is left aligned. Changing the alignment involves making a modification to your `includes/templates/YOURTEMPLATE/css/stylesheet.css`. 

Open the file and find the following:

```
#logo, .centerBoxContents, .specialsListBoxContents, .categoryListBoxContents, .centerBoxContentsAlsoPurch, .attribImg {float: left;}
```

Since this is a collection of several “selectors” (#logo, .centerBoxContents, etc) and in order not to interfere with the layout of other sections, split this into two separate statements and create a new selector/definition below it, like this:

```
.centerBoxContents, .specialsListBoxContents, .categoryListBoxContents, .centerBoxContentsAlsoPurch, .attribImg {float: left;}

#logo {float: left;}
```

To center the logo use `text-align: center;`.
To right align the logo use `float: right;`


