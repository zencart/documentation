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

The reason the instructions above recommend using the new name `newlogo.png` is to ensure that the old logo isn't cached. 

If you simply replace `includes/templates/YOURTEMPLATE/images/logo.gif` with your own logo using the same name, your browser will likely not pick up the change.  The reason for this is that the default configuration of browsers is to assume that you are a _user_, not a _developer_, so it tries to make your browsing experience faster by caching images.  Caching an image means retrieving it one time from the webserver to your local computer, and then using the local copy next time the image is needed, thereby saving the time required to retrieve it.

Since you are acting as a developer while you work on your site, you want to turn this behavior off.  The way this is done is specific to every browser and environment, so you'll have to do a web search to figure out how to do it with the tools you are working with.  

_The easiest way_ to get this working the first time is to use Google Chrome on a desktop computer, and follow these steps: 

- Right click and select Inspect. 
- Click the Network Tab
- Check the box that says Disable Cache
- With the Inspect window open, refresh the page being tested.

Once you have mastered this technique, you can figure out how to do it in other browsers and environments.  _It is particularly tedious to do this on a mobile device_, so I recommend using a desktop computer until you have more experience doing this sort of thing. 
