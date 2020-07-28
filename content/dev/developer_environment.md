---
title: Developer Environment
description: Zen Cart Developer Environment
description: Setting up your development environment
weight: 10
---

## Writing PHP code for Zen Cart requires no particularly special environment.

1. A PHP-aware IDE is useful. We use PhpStorm. 
   It's helpful if your editor honors the `.editorconfig` standard which sets out formatting standards for code files.
2. A LAMP stack is useful for running a local dev store. 
   Common options for this include XAMPP, WAMP/MAMP, and even Laravel Valet.

## Code Formatting

Line-endings in the github repo are (or are expected to be) `LF`.

Zen Cart uses [PSR-2 formatting](https://www.php-fig.org/psr/psr-2/) standards for "new" code.

OLDER code uses a "modified" PSR-2 which embraces "2 spaces" for indentation, and often leaves the "opening curly brace" of classes and functions on the prior line, instead of starting on a new line.

See [Coding Standards](/dev/contributing/coding_standards) for more details.

## Version Control

We encourage you to read the [section on Git](/dev/contributing/github_workflow/)
to learn about the workflow that the project uses.

## Retaining Default Directory Structure

By default you will get warnings if you don't rename the `admin` folder and delete the `zc_install` folder. 

To eliminate these warnings, create a file called `admin/includes/extra_configures/dev-skip_admin_rename.php` in which you add the following 2 entries:
```php
    define('ADMIN_BLOCK_WARNING_OVERRIDE', 'true');
    define('WARN_INSTALL_EXISTENCE', '0');
```

The filename prefix `dev-` is significant: the project `.gitignore` file is set to bypass files starting with that string.  So you can keep this new file in your fork of the Zen Cart project with no worries about accidentally checking it in.

## Configuration Keys 
It can be very helpful to see the `configuration_key` values for configuration entries while you are looking at your admin and thinking about writing code. 
The keys are shown in the [All Configs](/user/admin_pages/configuration/all/) page, but you can show them in your own admin, where they will also show any local configs you have added, using this procedure: 

- In your admin, go to the hidden page `configuration.php?gID=6`. 
- Look for the value *Admin configuration_key shows*.  
- Set this value to 1. 

Now, whenever you look at values in Admin > Configuration, you'll see the 
key value as well, which you will use in code. 

<img src="/images/show_keys.png" alt="Show Configuration Keys in Zen Cart" width="50%" />
<br><br>


Example: I am writing some code, and I need to see if the configuration allows add to cart on out of stock products.  Go to `Admin > Configuration > Stock` and select *Show Sold Out Image in place of Add to Cart*.  You'll see the key value is `SHOW_PRODUCTS_SOLD_OUT_IMAGE`.  So your code would be, 

```
if (SHOW_PRODUCTS_SOLD_OUT_IMAGE == '0') { 
  // Add to cart allowed 
...
```

## Overriding zc_install defaults

Since v1.5.6 the `zc_install` process allows you to specify a `DEVELOPER_MODE` environment variable, which if detected, will override two operations that occur at the end of `zc_install`: renaming the admin directory, and selecting an Admin password.

If `DEVELOPER_MODE` is enabled, then the `admin` directory will not be renamed, and the `Admin` user password will be set to `developer1` by default. NOTE: This only occurs in the development environment, and only on new-installs, thus is not related to live/production databases.

Since v1.5.7, the `zc_install/includes/localConfig.php` file allows you to specify default database credentials which are pre-filled when going through a fresh install process. 

NOTE: These defines only work if the `DEVELOPER_MODE` setting is enabled/detected.
