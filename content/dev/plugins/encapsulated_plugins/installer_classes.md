---
title: Installer Classes
description:  
weight: 30
layout: docs
---

## Installer Classes

In many cases you may not need anything custom done for a plugin beyond merely some SQL queries, which would be done in `install.sql` and removed via `uninstall.sql`. (But upgrades cannot be done merely via `.sql` files.)

However there may be times when a plugin needs to override the default installer behavior. Or handle database-changes during an Upgrade from a prior plugin version.

For example a plugin may need to check some pre-requisites before allowing installation, such as the availability of a PHP extension or maybe the plugin relies on another plugin being installed.

In these cases the plugin can define its own installer class that extends the base installer.

The class must be named `PluginInstaller.php` and be placed in the `Installer` directory.

e.g.

- zc_plugins

    - rewardPoints

        - v1.0.0

            - Installer

                - `PluginInstaller.php`

The skeleton of this class should look like :-

    <?php
    class PluginInstaller extends BasePluginInstaller
    {
    }

There are a number of methods that the custom installer class can override.

- prerequisitesCheck

FIXME
