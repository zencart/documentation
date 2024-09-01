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

Here's what should be in these files for version 2.1.0:

{{% version_files %}}

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
