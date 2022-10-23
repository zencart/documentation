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

- Admin access to the Version/Ping server (ping.zen-cart.com/dashboard).

- an up to date copy of both the branch that you are releasing, and the `main` branch. 

Once you have these things, you're almost ready to begin.

# Final Steps Before Beginning
## Update the version.php files: 

1. Edit the file `includes/version.php` and update the version.

1. Edit the file `zc_install/includes/version.php` and update the version.

1. Edit the file `zc_install/sql/install/mysql_zencart.sql` and update the version number in the `project_version` and `project_version_history` tables. 

1. Edit the file `zc_install/sql/updates/mysql_upgrade_zencart_158.sql` and update the version number in the `project_version` and `project_version_history` tables. 

1. Ensure the version number in `zc_install/includes/systemChecks.yml` is the current version. 

This can be confusing because sometimes the update letter is included and sometimes it isn't.  The thing to remember is that the database version does not include the letter, because the database doesn't change just because of a patch release.  

Here's what should be in these files for version 1.5.7b: 

|File | Version 
------|--------
|`includes/version.php`| `define('PROJECT_VERSION_MINOR', '5.7b');`|
|`zc_install/includes/version.php`|`define('PROJECT_VERSION_MINOR', '5.7b');`|
|`zc_install/sql/install/mysql_zencart.sql`|`project_version_patch1` for the two `Zen-Cart Main` rows should be `5.7b`|
|`zc_install/sql/install/mysql_zencart.sql`|`project_version_patch1` for the two `Zen-Cart Database` rows should be `5.7`|
|`zc_install/sql/updates/mysql_upgrade_zencart_157.sql`|Same two changes as install script above|
|`zc_install/includes/systemChecks.yml`|Top `checkDBVersion` block should be `version: '1.5.7'`|


## Copyright Updates

Do copyright updates in the following files: 

1. docs/INSTALL.TXT
1. docs/what's new file for this release
1. docs/changed files for this release

<div style="text-align:right;" id="next">
   <a class="btn btn-lg btn-primary mr-3 mb-4" href="/dev/release_process/initial_steps/">
        Next - Initial Steps<i class="fas fa-arrow-alt-circle-right ml-2"></i>
   </a>
</div>
