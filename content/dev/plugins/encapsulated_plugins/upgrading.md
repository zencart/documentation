---
title: Upgrading an encapsulated plugin 
description:  
weight: 90
layout: docs
---

Once you have created an encapsulated plugin, upgrading it is mostly a matter of creating a new version number under the plugin name, and then making your changes. 

So if the old plugin was structured like this: 

```
zc_plugins/MyPlugin/1.0.0
```

you can duplicate this to 

```
zc_plugins/MyPlugin/1.0.1
```

and make your changes.  Once you release, people will upload the new version and run through the upgrade process using Admin > Modules > Plugin Manager. 

**Note:** An `Installer/install.sql` file is ONLY run on NEW installs, not upgrades. 
So if your plugin makes any database changes, be sure to update:
- `Installer/install.sql` to include (in addition to any prior queries) any new things added by your upgraded version.
- `Installer/uninstall.sql` to include all (in addition to any prior) removals required to fully remove.
- `Installer/ScriptedInstaller.php` to use `executeUpgrade()` to perform any queries (if any) required by the new version. (This is the only way to apply db updates in an upgrade.)

