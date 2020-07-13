---
title: Installer Classes
description:  
weight: 30
layout: docs
---

## Installer Classes

For most cases the base installer class can be used without customisation to install a plugin.

However there may be times when a plugin needs to override the default installer behavior.

For example a plugin may need to check some pre-requisites before allowing installation.

This may be the availability of a php extension or maybe the plugin relies on another plugin being installed.

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
