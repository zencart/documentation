---
title: Upgrading an encapsulated plugin 
description:  
weight: 90
layout: docs
---

Once you have created an encapsulated plugin, upgrading it is 
mostly a matter of creating a new version number under the plugin name,
and then making your changes. 

So if the old plugin was structured like this: 

```
zc_plugins/MyPlugin/1.0.0
```

you can rename this to 

```
zc_plugins/MyPlugin/1.0.1
```

and make your changes.  Once you release, people will upload the new version and run through the upgrade process using Admin > Modules > Plugin Manager. 

**Note:** One constraint is that even if your first version did not use 
[SQL Installer Classes](/dev/plugins/encapsulated_plugins/sql_installation/#sql-installer-classes), your update must do so if there are database changes. 
The plain .sql files in the Installer folder are not run on an upgrade. 

