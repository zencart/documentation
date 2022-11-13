---
title: Converting a plugin to use encapsulation
description: 
weight: 80
layout: docs
type: codepage
---

**Note:** At the current time, only *admin* side plugins may be encapsulated.  The intention is to support catalog side plugin encapsulation in a future release. 

**Note** For simplicity, files like `license.txt`, `README.txt` and `docs` are omitted; no changes are made to those files, which are not deployed. 

Converting an older plugin to use the encapsulated architecture can be done 
following these steps: 

### 1. Create the plugin's file hierarchy. 

As a general rule, this just means moving the files you currently have in the 
plugin's top level folder under a new folder with the name 
<i>Plugin Name/Version</i>. 

For example, the [Mod List](https://www.zen-cart.com/downloads.php?do=file&id=2039) files, prior to conversion, were: 

```
./admin/includes/languages/english/extra_definitions/mod_list.php
./admin/includes/languages/english/mod_list.php
./admin/includes/extra_configures/mod_list.php
./admin/mod_list.php
```
**Note** On a live system the admin folder will have been renamed.

These become: 

```
./zc_plugins/ModList/1.4.0/admin/includes/languages/english/extra_definitions/mod_list.php
./zc_plugins/ModList/1.4.0/admin/includes/languages/english/mod_list.php
./zc_plugins/ModList/1.4.0/admin/includes/extra_configures/mod_list.php
./zc_plugins/ModList/1.4.0/admin/mod_list.php
```
**Note** It is not necessary to rename admin in the plugin directory hierarchy 

### 2. Add the Manifest 

Create a [manifest file](/dev/plugins/encapsulated_plugins/manifests/). In our example, this will be placed in 

```
./zc_plugins/ModList/1.4.0/manifest.php
```


### 3. Add the Plugin Installer script 

Create an [installer script](/dev/plugins/encapsulated_plugins/installer_classes/). 

In our example, this will be placed in 

```
./zc_plugins/ModList/1.4.0/Installer/PluginInstaller.php
```

### 4. (optional) Create install and uninstall files 

If the installer script you created above did not do the SQL operations 
required by the plugin, you can use [plain SQL files](/dev/plugins/encapsulated_plugins/sql_installation/).  

In our example, these will be placed in 

```
./zc_plugins/ModList/1.4.0/Installer/uninstall.sql
./zc_plugins/ModList/1.4.0/Installer/install.sql
```

### 5. Remove old files and update documentation 

Once you have put your the `admin`, `includes`, etc. folders under `zc_plugins`, *do not* duplicate them at the top level for older versions of Zen Cart. 
Instead, update the README file for your plugin with guidance like: 

```
If you are running a  Zen Cart installation older than 1.5.7, do not copy in the `zc_plugins` folder.  Instead, 
go to the `zc_plugins/YOURPLUGIN/VERSION/` folder and copy the `admin` and `includes` folders to your shopping cart (after renaming the `admin` folder.)
```
Alternately, you may mark your plugin as "1.5.7 (and above) only."

### 6. Final Result 

Now the file hierarchy looks  like this: 

```
./zc_plugins/ModList/1.4.1/admin/includes/languages/english/extra_definitions/mod_list.php
./zc_plugins/ModList/1.4.1/admin/includes/languages/english/mod_list.php
./zc_plugins/ModList/1.4.1/admin/includes/extra_configures/mod_list.php
./zc_plugins/ModList/1.4.1/admin/mod_list.php
./zc_plugins/ModList/1.4.1/manifest.php
./zc_plugins/ModList/1.4.1/Installer/uninstall.sql
./zc_plugins/ModList/1.4.1/Installer/PluginInstaller.php
./zc_plugins/ModList/1.4.1/Installer/install.sql
```

<hr>

### Things to watch for in the conversion 

a) Scope of variables in `extra_configures` and `extra_datafiles`

In the encapsulated plugin architecture, 
the files in `extra_configures` and `extra_datafiles` are run in the 
context of  the `FileSystem` class, 
and therefore any variables created will be scoped into that class and not the global scope.

This means if you have a file that was in `admin/includes/extra_configures/my_plugin.php` which created a variable (say, `$my_list`), this variable will not be available to the plugin anymore.  

Some options for overcoming this are: 

- Move the logic to a page specific init file. 

- Make the variables into defined constants (which by definition have global scope). 

b) Explicit `include` or `require` of storefront files 

TBD 
