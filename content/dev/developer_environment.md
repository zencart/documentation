---
title: Developer Environment
description: Zen Cart Developer Environment
description: Setting up your development environment
weight: 10
---

## Writing PHP code for Zen Cart requires no particularly special environment.

1. A PHP-aware IDE is very useful to highlight basic syntax errors. We use PhpStorm (commercial) but there are various free IDEs available.
   It's helpful if your editor honors the `.editorconfig` standard which sets out formatting standards for code files.
2. A LAMP stack is necessary to locally host a working development copy of your store. Common options for this include XAMPP, WAMP/MAMP, Laragon, and even Laravel Valet.

## Code Formatting

Line-endings in the github repo are (or are expected to be) `LF`.

Zen Cart uses [PSR-2 formatting](https://www.php-fig.org/psr/psr-2/) standards for "new" code.

OLDER code uses a "modified" PSR-2 which embraces "2 spaces" for indentation, and often leaves the "opening curly brace" of classes and functions on the prior line, instead of starting on a new line.

See [Coding Standards](/dev/contributing/coding_standards) for more details.

## Version Control

Zen Cart is developed using GitHub version control. We encourage you to create a GitHub account, firstly to become aware of project activity, and secondly to encourage your input. Read the [section on Git](/dev/contributing/github_workflow/)
to learn about the workflow that the project uses.

## Retaining the Default Directory Structure

By default, warnings are displayed if you don't rename the `admin` folder and delete the `zc_install` folder. 

To eliminate these warnings but maintain those folders you may create a file called `admin/includes/extra_configures/dev-skip_admin_rename.php` containing these two constants:
```php
    define('ADMIN_BLOCK_WARNING_OVERRIDE', 'true');
    define('WARN_INSTALL_EXISTENCE', '0');
```

The filename prefix `dev-` is significant: the project `.gitignore` file ignores files with this prefix so you can keep this new file in your GitHub fork of the zencart project without accidentally checking it in.

## Configuration Keys 
Every option that may be modified in the Admin screens is a constant stored in the database. It is very helpful to know the name of a constant (the `configuration_key`) when searching in code for their use or to use them in your own code. 

The keys used by Zen Cart are listed in the [All Configs](/user/admin_pages/configuration/all/) page, but that will not be a comprehensive list for **your** site as it does not include possible Plugins.  
However, the constant names may be displayed by enabling an admin option: 

- In your admin, each submenu under the Configuration menu has an url such as `admin/index.php?cmd=configuration&gID=1.`  
Manually change the gID to `gID=6` to display an additional page.
- Look for the value *Admin configuration_key shows*.  
- Set this value to 1. 

Now when editing an admin option, the constant name will be shown in the InfoBox title.

<img src="/images/show_keys.png" alt="Show Configuration Keys in Zen Cart" width="50%" />
<br><br>

Example use: I need to see if the configuration allows add to cart on out of stock products.  Go to `Admin > Configuration > Stock` and select *Show Sold Out Image in place of Add to Cart*.  You'll see the key value is `SHOW_PRODUCTS_SOLD_OUT_IMAGE`.  So your code would be, 

```
if (SHOW_PRODUCTS_SOLD_OUT_IMAGE == '0') { 
  // Add to cart allowed 
...
```

## Overriding the Installer (/zc_install) defaults

Since v1.5.6 the `zc_install` process allows you to specify a `DEVELOPER_MODE` environment variable, which if detected, will override two operations that occur at the end of `zc_install`: the auto-renaming of the admin directory, and auto-creation of an Admin password.

If `DEVELOPER_MODE` is enabled, then the `admin` directory will not be renamed, and the `Admin` user password will be set to `developer1` by default. 

**NOTE:** This only occurs in the development environment, and only on new-installs, thus is not related to live/production databases.

Since v1.5.7, the `zc_install/includes/localConfig.php` file allows you to specify default database credentials which are pre-filled when going through a fresh install process. 

**NOTE:** These defines only work if the `DEVELOPER_MODE` setting is enabled/detected.

A simple way of adding the `DEVELOPER_MODE` setting is to create a file inside `zc_install/includes/extra_configures`

e.g. `zc_install/includes/extra_configures/dev_mode.php`

## Overriding Email Sending
To prevent the sending of any emails at all
`define('DEVELOPER_OVERRIDE_EMAIL_STATUS', 'false')`

To send all emails to a specific testing address
`define('DEVELOPER_OVERRIDE_EMAIL_ADDRESS', 'root@localhost.com')`

The function zen_mail checks for these constants at the moment of processing an email and acts accordingly.

The function zen_mail could be called from the admin or the catalog, so the constants need to be available in both environments, ideally defined in one place and easily visible to avoid accidental copying to the production site.

One option is to place the constants in a storefront file  
e.g:
`/includes/extra_configures/dev-email_overrides.php`

and then "include" this file via an admin file  
e.g:
`ADMIN/includes/extra_configures/dev-email_overrides.php`

containing

```
<?php
include DIR_FS_CATALOG . DIR_WS_INCLUDES . 'extra_configures/dev-email_overrides.php';
```
When the admin environment detects these constants as defined, a message is displayed in the admin messageStack to that effect. 

## Innodb Settings 

The Zen Cart installer allows for setting a define to create all Database tables using InnoDb rather than MyIsam.

To enable this you need to add a define e.g. 

`define('USE_INNODB', true);`

Furthermore, you can also add another define that disables whether individual tables are not created as InnoDb tables and left as MyISAM tables. 

e.g. 

`define('INNODB_BLACKLIST', ['address_book']);`
