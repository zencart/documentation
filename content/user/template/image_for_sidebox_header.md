---
title: Can I use an image for a sidebox header 
description: Sidebox headers don't have to be text
category: template
weight: 10
---

Using an [image editor](/user/first_steps/useful_tools/#graphics-editors), create your image sets with a name for each sidebox you want to change. Upload to your server and save the images in `/includes/templates/YOURTEMPLATE/buttons/english/`.

In your `/includes/languages/YOURTEMPLATE/english.php` find this line of code:

```
define('BOX_HEADING_CATEGORIES', 'Categories'); 
```

Change it as follows:
```
define('BOX_HEADING_CATEGORIES', zen_image(DIR_WS_TEMPLATE . 'buttons/' . $_SESSION['language'] . '/' . 'image.gif', 'Your alt title text for heading'));
```

In your `/includes/languages/YOURTEMPLATE/english.php`, find this line of code:

```
define('BOX_HEADING_LINKS', '&nbsp;&nbsp;[more]'); 
```

Change it as follows:

```
define('BOX_HEADING_LINKS', ''); 
```

This method requires another edit which globally removes the `[more]` that follows all heading links.  However, but it does allow total flexibility in image type used for each replaced heading. In practice, heading images will usually be of the same type for consistency.
 
### Replacing background images for one or all sidebox headings:
You may want to keep the standard heading text, but change the background images.
If you want to replace the default Zen Cart background image to be used for all the sideboxes, use an image editor to create your image and save it to `/includes/templates/YOURTEMPLATE/images/` and upload it to your server.

Now open your `stylesheet.css`, find and edit the following rules:

```
.leftBoxHeading { 
  margin: 0em; 
  background: url(../images/background_image.jpg) no-repeat left top #ff6699; 
  padding: 0.5em 0.2em; 
}
.rightBoxHeading { 
  margin: 0em; 
  background: url(../images/background_image.jpg) no-repeat left top #ff6699; 
  padding: 0.2em 0em; 
} 
```

If you want a different background image for one sidebox heading, add to your stylesheet below the previous rules:

```
#categoriesHeading { 
  margin: 0em; 
  background: url(../images/categories_background_image.jpg) no-repeat left top #ff6699; 
  padding: 0.2em 0em; 
} 
```

Change the image file name in each of the URL property values, save the stylesheet and upload the image files to `/includes/templates/YOURTEMPLATE/images/` on your server.

