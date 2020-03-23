---
title: The Developers Template Overrides System 
description: Zen Cart Developers Template Overrides System 
category: template 
weight: 10
---

Zen Cart® features a template override system that allows you to customize the look and functionality of your store without having to modify core files. (Note: The override system is not yet available for `Admin` files, and is not yet available for some `Catalog` files.)

The template override system also allows you to change your store's look and functionality on a seasonal basis, for example, by creating multiple templates.

There are currently four components of the override system:

*   Language overrides
*   Template overrides
*   Module overrides
*   Sidebox overrides

## How the template override system works

To make use of the override system, first name your custom template. In the examples below, we will call this `YOURTEMPLATE`. You create a folder with this name in every directory that contains files you wish to modify. Place a copy of each file you wish to modify in the custom template directory at the same level; then modify this custom template copy, leaving the original file untouched.


**NOTE:** The override system does not extend to every file in your store. You can tell that a particular directory uses the override system by checking for the folder "classic" in that directory. Any directory that contains a classic subdirectory can be overridden.


For example, suppose you wish to make changes to the file `includes/languages/english.php`. You first create an override directory for your template at the same level, that is, in `includes/languages/`. Now you have a directory called `includes/languages/YOURTEMPLATE/`. Copy the file `includes/languages/english.php` to your override directory; now you have a file called `includes/languages/YOURTEMPLATE/english.php`. Make your desired changes to this file, and they will be picked up and used by the override system.

### Language overrides

You can override any file in the path `includes/languages/`. Create a folder named `YOURTEMPLATE` in each of the following directories:

*   `includes/languages`
*   `includes/languages/english`
*   `includes/languages/english/extra_definitions`
*   `includes/languages/english/html_includes`
*   `includes/languages/english/modules/order_total`
*   `includes/languages/english/modules/payment`
*   `includes/languages/english/modules/shipping`

Create a copy of any file you wish to modify, and place it in the appropriate custom template directory. For example, if you wish to modify the file `includes/languages/english/extra_definitions/some_file.php`, you would copy it to `includes/languages/english/extra_definitions/YOURTEMPLATE/some_file.php` and edit this file.

Repeat for every language your store uses.

### Template overrides

You can override any file in the path `includes/templates/template`default`. These are the files that determine the layout and HTML formatting of your web pages. Zen Cart® has two standard templates: `template`default` and `classic`. You can see these folders in the `includes/templates/` folder.

Of these two standard templates, only `template`default` contains a full set of files. Every other template contains only the files that differ from `template`default`; that is, only the files that have been modified. If your template does not contain a particular file, Zen Cart® will pull that file from `template`default`.

First, create the folder `includes/templates/YOURTEMPLATE`. As you customize your store, you will copy files from `includes/templates/template`default/` over to `includes/templates/YOURTEMPLATE/`, always preserving the directory structure.

For example, if you want to modify the CSS for your store, you will copy the file `includes/templates/template`default/css/stylesheet.css` to `includes/templates/YOURTEMPLATE/css/stylesheet.css`, and modify this copy.

### Module overrides

You can override files in the folder `includes/modules/`.

**NOTE:** The override system does not yet extend to files in the subfolders `order_total`, `pages`, `payment`, or `shipping`.


First, create the folder `includes/modules/YOURTEMPLATE`. As you customize your store, you will copy files from `includes/modules/` over to `includes/modules/YOURTEMPLATE/`.

For example, if you want to modify the product listing for your store, you will copy the file `includes/modules/product_listing.php` to `includes/modules/YOURTEMPLATE/product_listing.php`, and modify this copy.

### Sidebox overrides

You can override files in the folder `includes/modules/sideboxes/`. These are the boxes that appear in the left and right columns of your store.

First, create the folder `includes/modules/sideboxes/YOURTEMPLATE`. As you customize your store, you will copy files from `includes/modules/sideboxes/` over to `includes/modules/sideboxes/YOURTEMPLATE/`.

For example, if you want to modify the "More Information" sidebox, you will copy the file `includes/modules/sideboxes/more_information.php` to `includes/modules/sideboxes/YOURTEMPLATE/more_information.php`, and modify this copy.

## Selecting YOURTEMPLATE in the Admin

Login to your `Admin` panel and go to Tools > Template Selection.  You should see your new custom template(s) in the list. Select the template you wish to use.

Note: In order for the template to be on the list, the custom directory must be created in `/includes/templates/` and the `template_info.php` sets the

`$template_name = 'Template Name'`
