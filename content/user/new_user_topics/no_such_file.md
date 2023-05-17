---
title: I don't have the file YOURTEMPLATE/some-name
description: What if a template file is missing? 
category: new_user_topics
weight: 10
---

You're reading the instructions for a plugin or a FAQ page or a forum post
and it tells you to update 

```
includes/templates/YOURTEMPLATE/templates/tpl_product_info_display.php
```

and you say, "Wait a minute - that file doesn't exist in my cart!" 

First of all, let's review a few things: 

a) The FAQ [basic terms](/user/first_steps/basic_terms/) explains what YOURTEMPLATE means. 

b) The concept of a [default file](/user/first_steps/overrides/) which can be overridden. 

c) The FAQ [template overrides system](/user/template/template_overrides/) explains what template overrides are.


So now you know `YOURTEMPLATE` is an alias for the name of your template,
and you know that template override files are files that are modified 
to create a custom look for your store. 

So if your template is `responsive_sheffield_blue`, this file would be 
`includes/templates/responsive_sheffield_blue/templates/tpl_product_info_display.php`. 

If you are using the built-in default `responsive_classic` template, 
this file would be `includes/templates/responsive_classic/templates/tpl_product_info_display.php`. 

But what if the file still doesn't exist, even if you now know the real 
name of the file? 

Template files (the ones with `YOURTEMPLATE` - the [template name](/user/first_steps/basic_terms/#yourtemplate) in their path) are all
altered copies of the default file.

So if a referenced template file doesn't exist, you would create it from the default file.  

### Example (1.5.8) 
To create

```
includes/languages/english/YOURTEMPLATE/lang.header.php
```

copy
`includes/languages/english/lang.header.php` to `includes/languages/english/YOURTEMPLATE/lang.header.php`

### Example (1.5.7) 
To create

```
includes/languages/english/YOURTEMPLATE/header.php
```

copy
`includes/languages/english/header.php` to `includes/languages/english/YOURTEMPLATE/header.php`

### How do you find the default file? 

a) For files under `/includes/templates`, the default file is `includes/templates/template_default/FOLDER/FILENAME`. 

b) For all other files, the default file is one level above the template folder. 

If the templated file being referenced doesn't exist in your cart, you can 
create it by copying the original from the default file. 

[Learn more about default files](/user/first_steps/overrides/#default-files).

### What about language files? (1.5.8 and above) 

Language files are very similar.  If your language is French, and the instructions say, 

```
Update includes/languages/english/YOURTEMPLATE/lang.checkout_shipping.php
```

then you would want to update 

```
includes/languages/french/YOURTEMPLATE/lang.checkout_shipping.php
```

and if that file doesn't exist, you would create it from 

```
includes/languages/french/lang.checkout_shipping.php
```

### What about language files? (1.5.7 and below) 

Language files are very similar.  If your language is French, and the instructions say, 

```
Update includes/languages/english/YOURTEMPLATE/checkout_shipping.php
```

then you would want to update 

```
includes/languages/french/YOURTEMPLATE/checkout_shipping.php
```

and if that file doesn't exist, you would create it from 

```
includes/languages/french/checkout_shipping.php
```

# Installing a file

Unless you are creating these files directly on your server, 
you need to copy these files to your server.  Use your 
[FTP tool](/user/first_steps/useful_tools/#ftp-tools) to connect to your server, then go to your [webroot](/user/first_steps/how_do_i_install#what-is-my-webroot),
then to the folder where the file is supposed to exist. 

Example: 

- Your webroot is `/home/johndoe/public_html`
- Your template is `custom`
- The file you are changing is `includes/languages/custom/english.php`

Steps: 

- Using FTP, connect to `YOURSITE.com`.  
- Change directories so you get to the webroot.  
- Change directories from there so that you get to the folder for the file you are changing.  At this point, you will be in `/home/johndoe/public_html/includes/languages/custom`
- Transfer the file.

Here's what it looks like for a live store.  Click the image to make it larger if needed.  As you can see, the template is `bootstrap` and the webroot is `/home/thatsoft/public_html`.

<a href="/images/ftp_using_filezilla.png">
<img src="/images/ftp_using_filezilla.png" alt="FTP Using Filezilla" />
</a>

