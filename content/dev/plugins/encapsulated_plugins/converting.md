---
title: Converting an older plugin 
description:  
weight: 80
layout: docs
---

**Note** For simplicity, files like `license.txt`, `README.txt` and `docs` are omitted; no changes are made to those files, which are not deployed. 

Converting an older plugin to use the encapsulated architecture can be done 
following these steps: 

### 1. Create the plugin's file hierarchy. 

As a general rule, this just means moving the files you currently have in the 
plugin's top level folder under a new folder with the name 
<i>Plugin Name/Version</i>. 

For example, the Mod List files, prior to conversion, were: 

```
./admin/includes/languages/english/extra_definitions/mod_list.php
./admin/includes/languages/english/mod_list.php
./admin/includes/extra_configures/mod_list.php
./admin/mod_list.php
```
**Note** On the live system the admin folder will have been renamed.

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

