---
title: Will this plugin work with my Zen Cart version? 
description: How to determine if a plugin will interoperate with your cart
category: plugins
weight: 10
---

A frequently asked question on the Zen Cart forum is, "Does this plugin work with *latest Zen Cart version*?" 

Generally you can figure this out yourself by downloading and looking at the plugin. 

Assuming it was last updated for Zen Cart 1.5.x, check the following: 

- Does it overwrite any core files?  If no, then it will likely work as-is.

- If it does overwrite core files, and those core files have been changed since the plugin was last updated, you will need to merge those changes into your copy of the core file.  

- If it modifies template files, you will want to merge the changes required into your copy of the template file. 

If it hasn't been updated for a while, it *may* need updating for the current version of PHP.  See [PHP Warnings and Deprecated messages](/user/upgrading/php_warnings/) for some common fixes.

If the plugin was last updated prior to Zen Cart 1.5.0, you should probably assume it has been abandoned and avoid it. 

