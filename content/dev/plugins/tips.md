---
title: Tips on creating a plugin 
description: Zen Cart - Tips on creating a plugin 
category: plugins
weight: 1
---

## Security

It is wise to ensure that ALL your PHP plugin files include a line near the top which checks whether `IS_ADMIN_FLAG` is defined. This way if you have a file that's accessed via unauthorized methods then it will just abort. For example:

`if (!defined('IS_ADMIN_FLAG')) die();`

Other variations for specific use in either admin or catalog might check whether it is set to boolean `true`/`false`.


## Optimizing the use of Overrides 

There are built-in override capabilities in Zen Cart to prevent needing to edit some core files which would otherwise need updating.

(As a reminder, the override basics are covered in the storefront help; 
you may read 
[the introduction](/user/first_steps/overrides/), 
[the details](/user/new_user_topics/overrides/), 
and then 
[the summary](/user/template/template_overrides/).)

Some of the commonly-overlooked override capabilities are listed here:

### database_tables.php & filenames.php
Combine your extra details for these two files into one file, and then add it to both the storefront and the admin:

`includes/extra_datafiles/my-contribution-name_datafiles.php`

`admin/includes/extra_datafiles/my-contribution-name_datafiles.php`

(these will auto-load)

### stylesheet.css
`includes/templates/YOURTEMPLATE/css/styles_my-contribution-name.css`

(This will auto-load)

<hr>

## Other Resources 

- [Creating a menu item](/dev/code/creating_menu/)

- [Creating or altering tables](/dev/code/creating_tables/)

- [Building a form](/dev/code/forms/)


## Forum Resources 
If you run into trouble working on your plugin, you can always post your question on the [Contribution-Writing Subforum](https://www.zen-cart.com/forumdisplay.php?43-Contribution-Writing-Guidelines). 
