---
title: Prerequisites
weight: 20
layout: docs
category: release_process
---
To run the release process, you must have the following:

- Running at least PHP 8.1. (This means `php -v` must run without an alias and must show php 8.1 or higher.)  Here are [guidelines for upgrading to PHP 8.1 on a Mac](https://stitcher.io/blog/php-81-upgrade-mac). 

- `Maintainer` access to the Zen Cart github repository.

- A local copy of the [VersionStamper](https://github.com/zencart/versionstamper) application.

- Admin access to the main Zen Cart website 

- Admin access to the Server Manager (https://servermanager.zen-cart.com/)

- an up to date copy of the master branch for Zen Cart. 

- an up to date copy of the documentation repo. 

Once you have these things, you're almost ready to begin.

# Final Steps Before Beginning

## Prepare your branch 

Be sure your copy of the Github repo is up to date, and be sure you're on the right branch for building (either `master` or `prior-version-branch` for a patch).

Create a new branch specifically for the version file changes. 

## Update the versioning files: 

NOTE: If you are setting up a pre-release, please see [Pre-Release Notes](/dev/release_process/pre_release_notes/).


1. Edit the file `includes/version.php` and update the version.

1. Edit the file `zc_install/includes/version.php` and update the version.

**For patch releases or any release with no database change SKIP REMAINING VERSION FILE UPDATES.  Go to the next step.**

3. Edit the file `zc_install/sql/install/mysql_zencart.sql` and update the version number in the `project_version` and `project_version_history` tables. 

1. Edit the file `zc_install/sql/updates/mysql_upgrade_zencart_<current>.sql` and update the version number in the `project_version` and `project_version_history` tables. 

1. Ensure the version number in `zc_install/includes/systemChecks.yml` is the current version. 

1. Ensure the new version number has been added to `zc_install/ajaxLoadUpdatesSql.php`.

1. Ensure the new version number has been added to `zc_install/includes/modules/pages/database_upgrade/header_php.php`. 

This can be confusing because sometimes the patch number / update letter is included and sometimes it isn't.  The thing to remember is that the database version does not include the patch number / letter, because the database doesn't change just because of a patch release.  

Shortcut for editing these 7 files:

```
vi includes/version.php zc_install/includes/version.php zc_install/sql/install/mysql_zencart.sql zc_install/sql/updates/mysql_upgrade_zencart_200.sql zc_install/includes/systemChecks.yml zc_install/ajaxLoadUpdatesSql.php zc_install/includes/modules/pages/database_upgrade/header_php.php
```

Here's what should be in these files for version 2.0.0: 

|#|File | Version 
-|------|--------
|1|`includes/version.php`| `define('PROJECT_VERSION_MAJOR', '2');<br>define('PROJECT_VERSION_MINOR', '0.0');`|
|2|`zc_install/includes/version.php`|Same as above|
|3|`zc_install/sql/install/mysql_zencart.sql`|`project_version_major` and `project_version_minor` for the two `Zen-Cart Main` rows should be `2` and `0.0`.<br>`project_version_patch1` for the two `Zen-Cart Database` rows should be `New Installation-v200`<br><br>CHECK CAREFULLY - look at `project_version_major, project_version_minor, project_version_patch1,project_version_comment`|
|4|`zc_install/sql/updates/mysql_upgrade_zencart_200.sql`|`project_version_comment` for the two version rows should be `Version Update 1.5.8->2.0.0`<br><br>CHECK CAREFULLY - look at `project_version_major, project_version_minor, project_version_patch1,project_version_comment`|
|5|`zc_install/includes/systemChecks.yml`|Top `checkDBVersion` block should be `version: '2.0.0'`|
|6|`zc_install/ajaxLoadUpdatesSql.php`|`'2.0.0'=>array('required'=>'1.5.8'),`|
|7|`zc_install/includes/modules/pages/database_upgrade/header_php.php`|`$versionArray[] = '2.0.0';`|

There are other version related updates to do, but they're not part of the build, so they are detailed in [post release tasks](/dev/release_process/post_release/).

## For Major Releases - Update the Implementation Guide

The implementation guide (`docs/implementation-guide.pdf`) is part of the build and should be updated before the build begins.  See [Implementation Guide](/dev/release_process/implementation_guide/). 

This is mentioned on the next page as well as a reminder, since it's easy to forget. 

## For Major Releases - set the PHP Version range

Note: The actual PHP version we "support" is nowadays determined by what Laravel version we integrate. And that can be found in the `laravel` directory's `composer.json` file. Then translate it from "8.0.2" to "80002":   8.0.2 = 08.00.02 = 80002

Update these places: 

Uses of `PHP_VERSION_ID` (for the minimum version): 
- `zc_install/index.php`
- `includes/application_top.php`
- `admin/includes/application_bootstrap.php`
- `admin/includes/application_top.php`

Other Code Files: 

- `zc_install/includes/languages/en_us/main.php` (set `TEXT_ERROR_PHP_VERSION`)
- `zc_install/includes/systemChecks.yml` (set `checkPhpVersion`)
- `zc_install/index.php` (only change if zc_install itself needs a newer PHP version: we want zc_install to run for inspection even on older PHP)

Documentation Files: 
- [Server Requirements](/user/first_steps/server_requirements/#php-version) in `user/first_steps/server_requirements.md`.
- What's New file for this release, e.g. [What's New in 1.5.8](https://docs.zen-cart.com/release/whatsnew_1.5.8.html) under "About PHP Versions".  This file is in the `release` folder.
- `README.md` under [Zen Cart github home page](https://github.com/zencart/zencart)

Other considerations: 
- `/composer.json`
- `/laravel` - long before release, the bundled Laravel code should be matching PHP dependencies)
- Update github workflows so tests run on desired versions

## Copyright Updates

Do copyright updates in the following files: 

1. docs/INSTALL.TXT
1. what's new file for this release (Documentation site in `/release/` folder.)
1. changed files list for this release (Documentation site in `/release/` folder.)

## Check in! 

You'll want to check in all these changes so they get version stamped correctly.  Merge the branch you created for these changes. 



<div style="text-align:right;" id="next">
   <a class="btn btn-lg btn-primary mr-3 mb-4" href="/dev/release_process/initial_steps/">
        Next - Initial Steps<i class="fas fa-arrow-alt-circle-right ml-2"></i>
   </a>
</div>
