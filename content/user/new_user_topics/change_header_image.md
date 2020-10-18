---
title: How do I change the header background image 
description: My template uses a background image and I don't want it
category: new_user_topics
weight: 10
---

**Note:** This content does not apply to the responsive_classic template, and may not apply to your template. 

The [default template](/user/template/template_default/) and its derivatives use a background image in the header.

<img src="/images/header_bg.jpg" alt="Zen Cart background Image" />

You can see this by going to [Admin > Tools > Template Selection](/user/admin_pages/tools/template_selection/) and switching to *Classic Contemporary Green*.

By default Zen Cart uses `header_bg.jpg` for the name of this image, but you can use you own filename for the background image.

Using an [image editor](/user/first_steps/useful_tools/#graphics-editors), create a new background graphic and save it to 
`includes/templates/YOURTEMPLATE/images/yourheaderimage.jpg`. 

Now open your stylesheet.css and find or add the following code.

```
#logoWrapper {
  width:760px;
  height:110px;
  background-image:url('../images/yourheaderimage.jpg');
  background-repeat:no-repeat;
}
```

Change the file name to that of your own header image, adjust the width and height to those of your header image, save the stylesheet and upload both files to your server.


