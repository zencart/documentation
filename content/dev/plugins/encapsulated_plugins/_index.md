---
title: Encapsulated Plugins
description: A new architecture for writing plugins
category: plugins
weight: 10
---

In Zen Cart v1.5.7,  a Plugin Manager was added to begin allowing support for Admin-Only plugins using the new architecture.  This support has been incrementally improved in Zen Cart 1.5.8, 2.0.0 and 2.1.0, now providing support for storefront plugins as well.

The plugin architecture allows plugins to be encapsulated into a hierarchical directory structure that mimics the Zen Cart directory structure.  As such, plugin files no longer need to be placed within the various Zen Cart core directories, but rather exist in directories below a `zc_plugins` directory.

The admin's ***Modules :: Plugin Manager*** page allows for the plugin to be installed/un-installed and enabled/disabled.

***Note***: If your site is running a version of Zen Cart prior to 2.1.0, you'll need to apply these changes to some 'core' files for storefront/catalog plugins to operate correctly.  See https://gist.github.com/lat9/9deb64d3325081d18bb0db5534bcf142.


