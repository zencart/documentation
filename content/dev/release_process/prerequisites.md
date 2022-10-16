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

- ssh access to the main Zen Cart website (zen-cart.com), and the Version/Ping server (ping.zen-cart.com).

- an up to date copy of both the branch that you are releasing, and the `main` branch. 

The final steps before beginning the release process are: 

- Update the version.php files: 

1. Edit the file `includes/version.php` and check it in to update the version.

1. Edit the file `zc_install/includes/version.php` and check it in to update the version.


<div style="text-align:right;" id="next">
   <a class="btn btn-lg btn-primary mr-3 mb-4" href="/dev/release_process/initial_steps/">
        Next - Initial Steps<i class="fas fa-arrow-alt-circle-right ml-2"></i>
   </a>
</div>
