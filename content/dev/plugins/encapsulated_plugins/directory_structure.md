---
title: Directory Structure
description: Directory structure for encapsulated plugins 
weight: 1 
layout: docs
---

## Directory Structure

Plugins written for the new architecture will reside in the zc_plugins directory.
Within their directory, the plugins can add directories that mimic the main Zen Cart directories.
note how each plugin also has a versioned directory. This allows for automated upgrades and the possibility
of downgrading as well.

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
