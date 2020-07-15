---
title: Encapsulated Plugins
description: A new architecture for writing plugins
category: plugins
weight: 10
---

In Zen Cart v1.5.7,  a Plugin Manager was added to begin allowing support for Admin-Only plugins using the new architecture.

The plugin architecture allows plugins to be encapsulated into a hierarchical directory structure
that mimics the Zen Cart directory structure. 

So plugin files no longer need to be placed within the disparate Zen Cart core directories, 
but rather exist in directories below a `zc_plugins` directory.

A new plugin manager page allows for the plugin to be installed/un-installed and enabled/disabled.

**NOTE:** At the moment plugins only work for admin side code. Plugins for catalog will be introduced
in Zen Cart v1.5.8

