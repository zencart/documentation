---
title: Manifest Files
description:  
weight: 10
layout: docs
---

## Manifest Files

Each plugin must have a manifest.php file in the root of it's version directory.

e.g. 

  - zc_plugins
    - myPlugin
      -  v1.0.0
         - manifest.php
      
      
The  manifest file should look like

    <?php
    return [

        'pluginAuthor' => 'plugin author',
        'pluginVersion' => 'v1.0.0',
        'zcVersions' => ['v157'],
    ];

### pluginType

Currently we allow only two type, either `free` or `core`. All 3rd party plugins should be marked as
`free`

### pluginAuthor

A human readable string for the plugin author.

### pluginName

A human readable string for the name of the plugin.

### pluginDescripti

A human readable string describing the plugin.

### managed

All plugins written to the new v157 spefication should have `managed => true`. Legacy plugins
can add a manifest file where `managed => false` to allow for listings of plugins installed.

### zcVersions

An array of the Zen Cart versions the plugin supports.

### pluginGroups

`not currently supported` but will eventually support filtering in admin.

### @todo

manifest for file hashes to allow for security and auto upgrades etc.


