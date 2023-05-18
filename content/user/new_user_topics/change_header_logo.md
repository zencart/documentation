---
title: How do I change the logo or the logo alt text in the header? (1.5.8+)
description: Customizing your logo in 1.5.8 and above 
category: new_user_topics
weight: 10
---

**NOTE:** These instructions are for Zen Cart 1.5.8 and higher. If you need instructions for 1.5.7 or below, please see [Change Header Logo - 1.5.7](/user/new_user_topics/157_change_header_logo/).

## Storefront Header 

By default, Zen Cart uses `includes/templates/YOURTEMPLATE/images/logo.gif` for the filename of the logo image, but you can use your own filename for the logo.

**NOTE:** If your logo is already available as a .gif image, it's faster to just upload your logo by naming the file as logo.gif and replacing the logo.gif file on the server. Then refresh your browser cache (CTRL+R) to see it on your site. You may still want to update the image dimensions listed in the following instructions.

Using an [image editor](/user/first_steps/useful_tools/#graphics-editors), create your new logo and save it to `includes/templates/YOURTEMPLATE/images/yourname` and upload it to your server.

The name `yourname` will also include a file extension, such as `.png`, `.jpg`, etc. 

After creating your logo you can adjust the alt text, width, height, and image name in `includes/languages/english/YOURTEMPLATE/lang.header.php` (or `includes/languages/english/YOURTEMPLATE/header.php` in 1.5.7 or below). 

**NOTE:** In 1.5.8 and above, If you don't have the file `includes/languages/english/YOURTEMPLATE/lang.header.php`, then copy `includes/languages/english/lang.header.php` to `includes/languages/english/YOURTEMPLATE/lang.header.php` before editing.  See [What if I don’t have a file that some instructions mention?](/user/new_user_topics/no_such_file/)

For the purpose of this example, let's assume `yourname` is `newlogo.png`, and that the logo is 200px wide and 80px tall.

```
    'HEADER_ALT_TEXT' => 'my new alt text',
    'HEADER_LOGO_IMAGE' => 'newlogo.png',
    'HEADER_LOGO_WIDTH' => '200',
    'HEADER_LOGO_HEIGHT' => '80',
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

## Admin Header 
A similar change should be made in `admin/includes/languages/lang.english.php`, which contains the same four PHP define statements. You might use a different image in your admin. The filename mentioned here refers to a *different* file and location than the one used above for the storefront. See notes below.

```
    'HEADER_ALT_TEXT' => 'my new alt text',
    'HEADER_LOGO_IMAGE' => 'newlogo.png',
    'HEADER_LOGO_WIDTH' => '200',
    'HEADER_LOGO_HEIGHT' => '80',
```

The image itself should be placed in the `admin/images/` folder.
See [Using your logo on packing slips and invoices](/user/orders/high_res_logo) for more details.

If the logo in your admin is too wide for the white background, adjust the size of the div in `admin/login.php`. You'll see 3 lines that look like this:

```
      <div class="row">
        <div class="col-sm-offset-1 col-md-offset-3 col-lg-offset-4 col-xs-12 col-sm-10 col-md-6 col-lg-4 text-center">
          <div class="login-main-div login-box-shadow">
```

For desktop display, try adjusting `col-lg-4` to `col-lg-6`, for example, then adjust `col-lg-offset-4` to `col-lg-offset-3`.  Experiment with different values until you find one that works.

## Image Caching 

The reason the instructions above recommend using the new name `newlogo.png` is to ensure that the cache isn't used.

If you simply replace `includes/templates/YOURTEMPLATE/images/logo.gif` with your own logo using the same filename, your browser will likely not pick up the change immediately because of [caching](/user/new_user_topics/browser_caching/). 

## Related Articles 
- [Logos in HTML emails](/user/email/logo/) 
- [Using your logo on packing slips and invoices](/user/orders/high_res_logo)
