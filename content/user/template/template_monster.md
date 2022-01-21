---
title: Why does this plugin not work with Template Monster Templates?
description: Plugin works with template_default or responsive_classic, but not my template 
category: template
weight: 10
---

Zen Cart plugins often depend on built-in Zen Cart features, which are 
removed as an expedient by Template Monster developers.  

If you're using a Template Monster template and a change you are 
trying isn't working, you'll need to figure out the difference 
between the relevant default files and the files that your template 
is using, and restore the missing features.  

Sometimes the easiest way to do this is to back up the specific template file that doesn't work, and then copy in the version from `responsive_classic` (or `template_default`), and verify the operation of your plugin (just functionally - ignore the aesthetics).  Then see how much customization is required to make it look right. 

Note: Sometimes it's not even a plugin that's broken, it's core Zen Cart 
functionality.  If this is happening to you try just switching to `responsive_classic` (or `template_default`), and see if things work better.

Note: These issues are not exclusive to Template Monster; many other commercial template vendors use the same methods:
- deleting core code rather than correctly integrating with it.
- ignoring configuration settings and assume defaults rather than correctly coding for all possible configurations. 
- failing to stay up to date with Zen Cart core and PHP changes. 


