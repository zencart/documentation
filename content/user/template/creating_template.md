---
title: Creating a Custom Template 
description: Creating a Custom Template in Zen Cart
category: template 
weight: 10
---

To get ideas about building your own template, take a look at the 
other templates available for Zen Cart. 

{{< templates >}}

### Setting up your new template 
First, open 
`includes/templates/`
and create a new folder. You can call it anything you like, though it is best not to make it too long and to use underscores instead of spaces. We will call it `/YOURTEMPLATE` here, so everywhere we write 
`/YOURTEMPLATE` from now on, you should replace it with your own preferred folder name.

Next, you need to create the `template_info.php` file
and change your selected template.  
See [the template_info FAQ](/user/template/template_info/). 

### Building out your template 
Create an empty folder inside your new template directory and call it images so you should have `includes/templates/YOURTEMPLATE/images/`.

Next, copy the `includes/templates/template_default/css` directory and place the folder and its files in your new 
`includes/templates/YOURTEMPLATE/` folder.

You can also create the following empty folders inside your new template directory:

```
/common  
/sideboxes  
/templates  
```
When you've finished, your new file structure should look as follows:

```
includes  
   /templates  
       /YOURTEMPLATE  
          /common  
          /css  
             stylesheet.css  
          /images  
          /jscript  
          /sideboxes  
          /templates  
       template_info.php  
```

If you're basing your template on responsive_classic, it's recommended that you copy the complete jscript folder from responsive_classic into your custom template.

And if you need a base of CSS components, copy the contents of the css folder from the template you're basing from as well.

Upload your `/YOURTEMPLATE` folder to your server.  

Open your Admin panel and navigate to 
`Tools > Template Selection`.
Click the Edit button, then choose `YOURTEMPLATE` from the dropdown menu and click the Update button. Now, navigate to 
`Tools > Layout Boxes Controller`
and at the bottom of the page click the Reset button.

Your new template is now enabled and ready for you to customize. 
See [the customizing your template FAQ](/user/template/customizing_template/). 

### About Language Files

In the `/includes/languages/` folder there is also support for customizations for your new template too.

It is advisable to clone the `/includes/languages/english/html_includes/responsive_classic/` into a new folder named according to your custom template, such as `/includes/languages/english/html_includes/YOURTEMPLATE/`

### What about english.php?

It's advisable to leave the main `/includes/languages/english.php` untouched, and to put your customizations into a new file: `/includes/languages/YOURTEMPLATE/english.php` (ie: if you want to customize the text for `FOOTER_TEXT_BODY`, put *just* the define for `FOOTER_TEXT_BODY` into your `YOURTEMPLATE/english.php` file (no need to copy the entire file; in fact, upgrades are easier if you only put the individual changes there).

**NOTE:** See [Basic Terms](/user/first_steps/basic_terms/) for an 
explanation of `YOURLANGUAGE` and `YOURTEMPLATE` if these terms are 
unfamiliar. 

