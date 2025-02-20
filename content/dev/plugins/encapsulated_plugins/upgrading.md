---
title: Upgrading an encapsulated plugin 
description:  
weight: 90
layout: docs
---

Once you have created an encapsulated plugin, upgrading it is mostly a matter of creating a new version number under the plugin name, and then making your changes. 

So if the old version was structured like this: 

```
zc_plugins/MyPlugin/1.0.0
```

you can duplicate this to 

```
zc_plugins/MyPlugin/1.0.1
```

and make your changes. 

If you're using GitHub for your plugin, then commit the new directory to your repository before making new changes for the new version. 

Once you release, end-users will upload the new version-number directory to their server and run through the upgrade process using Admin > Modules > Plugin Manager.

**Note:** An `Installer/install.sql` file is ONLY run on NEW installs, not upgrades. 
So if your plugin makes any database changes, be sure to update:
1. `Installer/ScriptedInstaller.php` to use `executeUpgrade()` to perform any queries (if any) required by the new version. (This is the **only way** to apply db updates in an upgrade.)
2. `Installer/install.sql` (IF used) to include (in addition to any prior queries) any new things added by your upgraded version.
3. `Installer/uninstall.sql` (IF used) to include all (in addition to any prior) removals required to fully remove.

TO BE CLEAR: The `ScriptedInstaller.php` (and `install.sql` and `uninstall.sql` if they exist (they're not required)) MUST be capable of handling BOTH fresh installs AND upgrades across ALL versions that your plugin supports. THERE IS NO "INCREMENTAL" UPGRADE SUPPORT BASED ON FILENAMES OR VERSION NUMBERS. Any "incremental" upgrade steps would be coded into your ScriptedInstaller.php script, taking care of doing all requisite dependency checks there.
