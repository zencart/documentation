---
title: How do I disable plugin version checking? 
description: I don't want to see the message "A NEW VERSION OF THIS PLUGIN IS AVAILABLE"
category: plugins
weight: 10
---

Plugins that call the function `plugin_version_check_for_updates` will phone home to the Zen Cart ping server and check for version updates.  Developers may refer to [Plugin Tips](/dev/plugins/tips/#automatic-new-version-checks) for details. 

This messaging may or may not always be desirable; for modules with external interfaces, it can be critical to stay up to date, but for plugins that do other things, updates may be optional. 

If you do want to disable checking for a particular plugin, try the following: 

- Check the plugin's Admin page and see if it has a setting to disable version checking.
- Comment out the call to `plugin_version_check_for_updates` in this plugin's code.

