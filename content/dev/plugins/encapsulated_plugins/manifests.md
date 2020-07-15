---
title: Manifest Files
description:  
weight: 10
layout: docs
---

## Manifest Files

Each plugin must have a `manifest.php` file in the root of its version directory.

e.g. 

  - zc_plugins
    - myPlugin
      -  v1.0.0
         - manifest.php
      
      
The  manifest file should look like:

```
<?php
return [
    'pluginVersion' => 'v3.0.0',
    'pluginName' => 'Display logs',
    'pluginDescription' => 'Display and manage Zen Cart log files.',
    'pluginAuthor' => 'Vinos de Frutas Tropicales (lat9)',
    'pluginId' => 1583, // ID from Zen Cart forum
    'zcVersions' => ['v157'],
    'changelog' => '', // online URL (eg github release tag page, or changelog file there) or local filename only, ie: changelog.txt (in same dir as this manifest file)
    'github_repo' => '', // url
    'pluginGroups' => [],
];
```

### pluginVersion

The version of this plugin. It should match the version number entered when submitting the plugin to the Plugins Library on the Zen Cart forum.

### pluginName

A human readable string for the name of the plugin.

### pluginDescription

A human readable string describing the plugin.

Flagrant advertising is not permitted.

### pluginAuthor

A human readable string for the plugin author.

### PluginId

The `id` number assigned by the Zen Cart forum site when submitting the plugin for review.
e.g. https://www.zen-cart.com/downloads.php?do=file&id=1583
This is used by the store's Plugin Manager to check for whether new versions have been submitted.

The Plugin Manager only alerts about new versions of this plugin if the store's Zen Cart version matches one of the versions specified in a given update on the Zen Cart Plugins Library. 

Set it to `0` if you're writing a plugin that you're not submitting to the Plugins Library. (eg: a commercial plugin)

### changelog

Online URL (eg github release tag page, or changelog file there) or local filename only, ie: changelog.txt (in same dir as this manifest file)

### github_repo

A link to the plugin's github repo, if one exists.

### zcVersions

An array of the Zen Cart versions the plugin supports. (eg: `['v157']`, or `['v157','v158']`).

### pluginGroups

`not currently supported` but will eventually support filtering the display of plugins in the admin.
