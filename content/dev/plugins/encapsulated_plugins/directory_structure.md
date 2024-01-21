---
title: Directory Structure
description: 
weight: 1 
layout: docs
---

## Directory Structure

Plugins written for the new architecture will reside in the `zc_plugins` directory.

Within their directory, plugin authors can add subdirectories that mimic the main Zen Cart directories.

Note how each plugin starts with a versioned directory. 
This allows for automated upgrades and the possibility of downgrading as well.

Note that the `admin` folder *must* be called `admin` here (not renamed). 

e.g.

- zc_plugins

    - rewardPoints

        - v1.0.0
            - manifest.php
      
            - Installer

            - admin
      
                - includes
                    - auto_loaders
                    - classes
                    - extra_datafiles
                    - init_includes
                    - javascript
                    - languages
      
        - v1.0.1
            - manifest.php
      
            - Installer

            - admin
      
                - includes
                    - auto_loaders
                    - classes
                    - extra_datafiles
                    - init_includes
                    - javascript
                    - languages
      

**NOTE:** Zen Cart only supports admin-side plugins at this time.

ALSO: None of this works before Zen Cart v1.5.7: Plugins for prior versions must be installed directly into the main Zen Cart directory structure.

**NOTE:** The `Installer` folder is optional; you can embed the installation logic in your plugin if you prefer.  See [Installer Classes](/dev/plugins/encapsulated_plugins/installer_classes/) and [Plugin SQL Installation](/dev/plugins/encapsulated_plugins/sql_installation/) for details on using the `Installer` folder. 

**NOTE on JavaScript loading:** naming your JavaScript file the same name as your PHP file name will make it automatically load.  If you have additional .js files to load, give them names starting with the PHP file name followed by an underscore.  For example, if you create a file called `admin/rewards.php`, the autoloader will load `admin/includes/javascript/rewards.js`, as well as any JavaScript file whose name matches the pattern `admin/includes/javascript/rewards_*.js`, e.g. `admin/includes/javascript/rewards_sha-256.js`.
