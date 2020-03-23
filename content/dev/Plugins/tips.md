---
title: Tips on creating a plugin 
description: Zen Cart - Tips on creating a plugin 
category: plugins
weight: 1
---
## Override Secrets 

There are built-in override capabilities in Zen Cart to prevent needing to edit some core files which would otherwise need updating.

Some of the commonly-overlooked override capabilities are listed here:

### database_tables.php & filenames.php
Combine your extra details for these two files into one file, and then add it to both the storefront and the admin:

`includes/extra_datafiles/my-contribution-name_datafiles.php`

`admin/includes/extra_datafiles/my-contribution-name_datafiles.php`

(these will auto-load)

### stylesheet.css
`includes/templates/YOURTEMPLATE/css/styles_my-contribution-name.css`

(This will auto-load)

<hr />

### Forum Resources 
If you run into trouble working on your plugin, you can always post your question on the [Contribution-Writing Subforum](https://www.zen-cart.com/forumdisplay.php?43-Contribution-Writing-Guidelines). 
