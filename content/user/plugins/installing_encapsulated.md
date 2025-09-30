---
title: Installing an encapsulated plugin
description: Adding an encapsulated plugin to your store
category: plugins
weight: 10
---

This help file describes newer "encapsulated" plugins that are installed under `zc_plugins`.  For older plugines which are copied directly into the `includes` and `admin` folders, see [How to install a plugin](/user/plugins/how_to_install_a_plugin).

Encapsulated plugins have been supported in Zen Cart since version 1.5.7, as a way to make plugin installation and maintenance easier for end users.  Developers may learn more by reading [the encapsulated plugin documentation](/dev/plugins/encapsulated_plugins).

Encapsulated plugins are controlled using the [Plugin Manager](/user/admin_pages/modules/plugin_manager).

## Getting Started

Before you start, you'll need to verify that you have some things.

*   Plugins are provided in zip format, so you'll need a tool to unzip the file.
*   You'll need a tool to transfer the files from your local PC to your webserver.
*   You'll need a simple text editor to do customizations to files

## Installing 

* Copy the files from the unzipped plugin into the `zc_plugins` folder in your cart.  

* In your admin, navigate to Modules > Plugin Manager 

* Select the new plugin you wish to install.

* Press the Install button.  There may be more actions required, but they will all the done under your admin; no filesystem modifications are needed.

