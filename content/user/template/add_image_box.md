---
title: Add image to sidebox or centerbox
description: Using a sidebox or centerbox to show product images 
category: template
weight: 10
---

The exact method will depend upon whether you are creating a small image to be repeated, or a image that will either span the box or is intended to be centered within it. 

Firstly, create your image and place it in the images directory of your template.

Then find the following blocks in your CSS:

For adding the image to the center boxes:
```
.centerBoxWrapper {
    border: 1px solid #9a9a9a;
    height: 1%;
    margin: 1.1em 0;
    }
```

For adding to the left and/or right sideboxes:
```
.leftBoxContainer, .rightBoxContainer {
    margin: 0em;
    border: 1px solid #9a9a9a;
    border-bottom: 5px solid #336633;
    margin-top: 1.5em;
    }
```

The above CSS is taken from the default template and may vary depending upon which template you are using and what modifications have been made to it.

Then add the following CSS to the appropriate block
```
   /* create free space at the bottom of the box in which to display the image */
    padding-bottom: 20px;
    /* add the image to the boxes background */
    background-image: url(../images/box_bg.jpg);
    /* position the image at the bottom and center of the box */
    background-position: bottom center;
    /* EITHER set the image to not repeat */
    background-repeat: no-repeat;
    /* OR set it to repeat horizontally */
    background-repeat: repeat-x;
```

You can use the same image for both center and sideboxes if you wish. Any excess width will fall outside the box and not be displayed.

