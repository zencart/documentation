---
title: How do I change the logo or the logo alt text in the header?
description: Changing the header logo in Zen Cart 
category: new_user_topics
weight: 10
aliases: 
    - /user/new_user_topics/change_powered_by/
---

By default, Zen Cart uses `includes/templates/YOURTEMPLATE/images/logo.gif` 
for the name of the logo image, but you can use you own filename for the logo.

Using an [image editor](/user/first_steps/useful_tools/#graphics-editors), create your new logo and save it to `includes/templates/YOURTEMPLATE/images/yourname` and upload it to your server.

The name `yourname` will also include a file extension, such as `.png`, `.jpg`, etc. 

After creating your logo you can adjust the alt text, width, height, and image name in `includes/languages/english/YOURTEMPLATE/header.php`

**Note:** If you don't have the file `includes/languages/english/YOURTEMPLATE/header.php`, then copy `includes/languages/english/header.php` to `includes/languages/english/YOURTEMPLATE/header.php` before editing.  See [What if I don’t have a file that some instructions mention?](/user/new_user_topics/no_such_file/)

For the purpose of this example, let's assume `yourname` is `newlogo.png`, and that the logo is 200px wide and 80px tall.

```
define('HEADER_ALT_TEXT', 'My new alt text');
define('HEADER_LOGO_WIDTH', '200px');
define('HEADER_LOGO_HEIGHT', '80px');
define('HEADER_LOGO_IMAGE', 'newlogo.png');
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

To center the logo use `text-align: center;`

To right align the logo use `float: right;`

## Image Caching 

What if after you upload a new logo, you don't see any change on the website? This is due to [image caching](/user/new_user_topics/image_caching).