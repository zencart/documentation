---
title: Pre-Release Notes 
weight: 8 
layout: docs
category: release_process
---

Note: This step only apples to pre-release version updates, which are done at the time of initiation of a new release. 

If you are doing official release, please skip this step and go to the [next step](/dev/release_process/dependency_checks/). 

## Git Work

The master branch is now the current release.  If a patch is being done from a release in the past, create a branch for that patch. 

## Versioning files 

Before doing the version updates, create a new branch specifically for these changes. 

Here's what should be in these files for version 2.0.0-alpha1:

|#|File | Version |
-|-----|---------|
|1|`includes/version.php`| `define('PROJECT_VERSION_MINOR', '0.0-alpha1');`|
|2|`zc_install/includes/version.php`|`define('PROJECT_VERSION_MINOR', '0.0-alpha1');`|
|3|`zc_install/sql/install/mysql_zencart.sql`|`project_version_major` and `project_version_minor` for the two `Zen-Cart Main` rows should be `2` and `0.0-alpha1`.<br>CHECK CAREFULLY - look at all rows|
|4|`zc_install/sql/updates/mysql_upgrade_zencart_200.sql`|`project_version_major` and `project_version_minor` should match the install file.  `project_version_comment` for the two version rows should be `Version Update 1.5.8->2.0.0-alpha1`<br><br>CHECK CAREFULLY - look at all rows|
|5|`zc_install/includes/systemChecks.yml`|Top `checkDBVersion*` block should look for `version: '2.0.0'`|
|6|`zc_install/ajaxLoadUpdatesSql.php`|`'2.0.0'=>array('required'=>'1.5.8'),`||
|7|`zc_install/includes/modules/pages/database_upgrade/header_php.php`|`$versionArray[] = '2.0.0';`|

Shortcut for editing these 7 files: 

```
vi includes/version.php zc_install/includes/version.php zc_install/sql/install/mysql_zencart.sql zc_install/sql/updates/mysql_upgrade_zencart_200.sql zc_install/includes/systemChecks.yml zc_install/ajaxLoadUpdatesSql.php zc_install/includes/modules/pages/database_upgrade/header_php.php
```

## PHP Compatibility 

If the new version has different PHP compatibility ranges than the prior one, be sure to update: 

- `composer.json`
- The [Server Requirements](https://docs.zen-cart.com/user/first_steps/server_requirements/#php-version) help document
- The What's New file for the release in [Release Docs](https://docs.zen-cart.com/release)

<div style="text-align:right;" id="next">
   <a class="btn btn-lg btn-primary mr-3 mb-4" href="/dev/release_process/dependency_checks/">
        Next - Dependency Checks<i class="fas fa-arrow-alt-circle-right ml-2"></i>
   </a>
</div>
