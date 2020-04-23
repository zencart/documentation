---
title: Developer Environment
description: Zen Cart Developer Environment
description: Setting up your development environment
weight: 1
---

## Writing PHP code for Zen Cart requires no particularly special environment.

1. A PHP-aware IDE is useful. We use PhpStorm.
2. A LAMP stack is useful for running a local dev store. Common options for this include XAMPP, WAMP/MAMP, and even Laravel Valet.

## Code Formatting

Zen Cart uses [PSR-2 formatting](https://www.php-fig.org/psr/psr-2/) standards for "new" code. Older code uses a "modified" PSR-2 which embraces "2 spaces" for indentation, and often left the "opening curly brace" on the prior line, instead of starting on a new line.

See [Coding Standards](/dev/contributing/coding_standards) for more details.

## Version Control

We encourage you to read the [section on Git](/dev/contributing/github_workflow/)
to learn about the workflow that the project uses.

## Preserving Directory Structure

By default you will get warnings if you don't rename the `admin` folder and delete the `zc_install` folder. 

To eliminate these warnings, create a file called `admin/includes/extra_configures/dev-skip_admin_rename.php`.  Add the following 2 entries:
```php
    define('ADMIN_BLOCK_WARNING_OVERRIDE', 'true');
    define('WARN_INSTALL_EXISTENCE', '0');
```

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

