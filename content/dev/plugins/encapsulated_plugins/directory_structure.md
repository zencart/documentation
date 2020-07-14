---
title: Directory Structure
description: Directory structure for encapsulated plugins 
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
      
            - admin
      
                - includes
                    - auto_loaders
                    - init_includes
                    - extra_datafiles
                    - classes
                    - languages
      
            - catalog
      
                - includes
      
                    - functions
      
                        - extra_functions
      
                - templates
                - etc

        - v1.0.1
            - manifest.php
      
            - admin
      
                - includes
                    - auto_loaders
                    - init_includes
                    - extra_datafiles
                    - classes
                    - languages
      
            - catalog
      
                - includes
      
                    - functions
      
                        - extra_functions
      
                - templates
                - etc

**NOTE:** While these examples mention the `catalog` subdirectory, Zen Cart v1.5.7 only supports admin-side plugins at this time.

ALSO: None of this works before Zen Cart v1.5.7: Plugins for prior versions must be installed directly into the main Zen Cart directory structure.
