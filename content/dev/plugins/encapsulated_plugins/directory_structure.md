---
title: Directory Structure
description: 
weight: 1 
layout: docs
---

## Directory Structure

Plugins written for the new architecture will reside in the `zc_plugins` directory.

Within their directory plugin authors can add subdirectories that mimic the main Zen Cart directories.

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
      
            - catalog
      
                - includes
      
                    - functions
      
                        - extra_functions
      
                - templates
                - etc

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
      
            - catalog
      
                - includes
      
                    - functions
      
                        - extra_functions
      
                - templates
                - etc

**NOTE:** While these examples mention the `catalog` subdirectory, Zen Cart v1.5.7 only supports admin-side plugins at this time.

ALSO: None of this works before Zen Cart v1.5.7: Plugins for prior versions must be installed directly into the main Zen Cart directory structure.

**NOTE:** The `Installer` folder is optional; you can embed the installation logic in your plugin if you prefer.  See [Installer Classes](/dev/plugins/encapsulated_plugins/installer_classes/) and [Plugin SQL Installation](/dev/plugins/encapsulated_plugins/sql_installation/) for details on using the `Installer` folder. 

**NOTE on javascript loading:** naming your javascript file the same name as your file name will load the  .js file.  if you have addtional .js files to load, preface the names by the file name followed by an underscore.  for example, if your plugin has a script called `admin/rewards.php`, the ZC autoloader will load `admin/includes/javascript/rewards.js`.  In addition, the autoloader will also load anything that starts with the filename, ie `admin/includes/javascript/rewards_sha-256.js`.
