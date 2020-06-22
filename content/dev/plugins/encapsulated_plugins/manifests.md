---
title: Manifest Files
description:  
weight: 10
layout: docs
---

## Manifest Files

Each plugin must have a manifest.php file in the root of its version directory.

e.g. 

  - zc_plugins
    - myPlugin
      -  v1.0.0
         - manifest.php
      
      
The  manifest file should look like

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

The version of this plugin. 

### pluginName

A human readable string for the name of the plugin.

### pluginDescripti

A human readable string describing the plugin.

### pluginAuthor

A human readable string for the plugin author.

### PluginId

The id assigned by the Zen Cart Website 
e.g. https://www.zen-cart.com/downloads.php?do=file&id=1583
This is used to do `call home` checking for new versions.

### changelog

online URL (eg github release tag page, or changelog file there) or local filename only, ie: changelog.txt (in same dir as this manifest file)

### github_repo

A link to the plugins github repo, if one exists.

### zcVersions

An array of the Zen Cart versions the plugin supports.

### pluginGroups

`not currently supported` but will eventually support filtering in admin.
