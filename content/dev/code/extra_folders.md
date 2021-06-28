---
title: Extra Folders 
description: extra_datafiles, extra_definitions, extra_functions and extra_configures 
category: code
weight: 10
---

Files in these folders are autoloaded: 

```
includes/extra_datafiles/
includes/languages/english/extra_definitions/
includes/functions/extra_functions/
includes/extra_configures/
admin/includes/extra_datafiles/
admin/includes/languages/english/extra_definitions/
admin/includes/functions/extra_functions/
admin/includes/extra_configures/

```

Note that the folder `/extras` at the root of Zen Cart is 
a set of utilities, not autoloads.

Autoloads are designed to make upgrades easier since using them means fewer core file edits. 

The usage of these folders is as follows: 

- `includes/extra_datafiles`: definitions of table names and PHP files which have been added.  Using this folder means not having to update the core files `includes/database_tables.php` and `includes/filenames.php`.

- `includes/languages/english/extra_definitions`: language constants which have been added.  Using this folder means not having to update the core files `includes/languages/english.php`. 

- `includes/functions/extra_functions` - global functions which have been added.  Using this folder means not having to update `includes/init_includes/init_general_funcs.php`. 

- `includes/extra_configures` - global configuration settings which have been added.  Using this folder means not having to modify `includes/configure.php`. 

The admin folders use the same pattern. 

