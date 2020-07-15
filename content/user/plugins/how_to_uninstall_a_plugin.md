---
title: How to uninstall a plugin
description: Backing out a plugin
category: plugins
weight: 10
---

Uninstalling a plugin is harder than installing one; there are no
two ways around it. 


## Reading the instructions

Plugins often have their own uninstall instructions.  When this is
the case, follow the instructions. 

Otherwise, keep reading. 

## Basic Steps 

1. If you have a backup from before you did the installation, simply 
restore the backup.  If you don't - well, now you see the importance
of [creating a backup](/user/running/backup/).

1. Remove any NEW files that you added in the process of installing the plugin.   A NEW file is a file that doesn't exist in the default distribution of Zen Cart.  These files can simply be deleted. 

1. Remove any modifications to EXISTING files that you performed as part of installing the plugin.  A plugin might modify a core file (part of the default distribution of Zen Cart) or a template file (a file you have put in one of your template folders as an override).  These changes will need to be removed. 

1. Undo any changes to the database. Ideally there will be an uninstall
script.  **THIS IS THE MOST DANGEROUS PHASE OF THE PROCESS**, so be sure
you make a backup first. 

1. If you need help during this process, post to the support thread
for the plugin.  This can be found on the plugin's page in the 
[Plugins Library](https://www.zen-cart.com/downloads.php). 

## Too Much? 
If this sounds like too much for you, the best route is to go onto the 
[Zen Cart Commercial Help Wanted forum](https://www.zen-cart.com/forumdisplay.php?138-Commercial-Help-Wanted) and hire a pro. 

