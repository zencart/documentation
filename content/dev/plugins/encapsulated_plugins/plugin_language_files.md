---
title: Plugin Installer Language Files
description:  
weight: 20
layout: docs
---

## Plugin Installer Language Files

While most language constants for the plugin installer are managed internally there will be cases where a plugin
needs to define some of its own language defines.

For example, if the plugin needs to test some pre-requisites before installing, the error messages for when those
pre-requisites fail will need to be defined.

In these cases the plugin system allows for loading custom language files.

The main custom language file would reside in the `plugin version directory`/languages/`language name`/main
.php file.

e.g.

- zc_plugins

    - rewardPoints

        - v1.0.0

            - Installer

            - languages

                - english

                    - `main.php`


If the plugin needs more customisation and wants to split off other language defines into separate files it may
also load the language files separately.

A helper method in the installer class can be used to do this.

e.g.

    $this->loadInstallerLanguageFile('myFile.php');

Remember, we are talking here about language defines that are only used during installation. Loading
of language files needed by the plugin itself are handled differently.


