---
title: What's New in Version 2.2.0
description: Features and fixes in Zen Cart 2.2.0
category: release
weight: 100
layout: docs
noindex: yes
---

{{% release_welcome %}}

About PHP versions
==================

Zen Cart v2.2.x is designed for PHP 8.0 to 8.4, with MySQL 5.7.8+ (or MariaDB 10.2.7+) and Apache 2.2/2.4.

Upgrade Instructions
====================

See the [online docs](/user/upgrading/) for upgrading advice, including Release-Specific considerations to note regarding this version. 
  
This document only mentions the actual changes specific to v2.2.x since v2.1.0.

All Versions
------------

If you are upgrading from the prior release, please do a [standard site upgrade](https://docs.zen-cart.com/user/upgrading/detailed_upgrading/).

If you are upgrading from a release which is older than the prior release, you may wish to consider starting again using a [database only upgrade](https://docs.zen-cart.com/user/upgrading/db_only_upgrade/).

Many older templates are going to be difficult to bring forward. If you are using an older template - especially one that is not [responsive](https://docs.zen-cart.com/user/template/responsive/) - you may wish to consider migrating to [Responsive Classic](https://docs.zen-cart.com/user/template/responsive_classic/) or [Bootstrap](https://docs.zen-cart.com/user/template/bootstrap/).

Be sure to review all the links in this article, including tips on staging the upgrade in a separate directory/folder.

If you are using Addons/Plugins that use modified versions of core Zen Cart files, you must compare those plugin files to the original Zen Cart files of the version for which those plugins were built, to identify the modifications. Subsequently you must replicate those modifications in the release version of the file. Be sure to check the plugin's support thread to see if a new version has been released since the one you installed before.

Always review the [Release Specific Upgrade Considerations](https://docs.zen-cart.com/user/upgrading/release_specific_upgrade_considerations/) for the release you are upgrading to all the way back to the release you are upgrading from.

CHANGELOG - List of Changed Files
=================================

For a list of files that have been changed since v2.0.1, see the [changed_files-v2.2.0](/release/changed_files-v2-2-0/) document.

Upgrading to a Responsive Template
==================================

If your site doesn't look good on a mobile phone or a tablet, it's likely because it's using an older non-responsive template. You can read about [Responsive Templates](https://docs.zen-cart.com/user/template/responsive/) on the help site to learn more.

If you are upgrading an older site, we recommend that you use a responsive template (rather than `template_default` or any older non-responsive template) as the starting point for your upgraded site. Both the [Responsive Classic](https://docs.zen-cart.com/user/template/responsive_classic/) and [Bootstrap](https://docs.zen-cart.com/user/template/bootstrap/) templates are good candidates.

Upgrader Notes About Changes to `template_default`
=================================================

Upgraders should make sure they update *BOTH* `template_default` *AND* their custom templates as described here

In Zen Cart the `template_default` directory contains the master copy of all storefront page templates.

The normal procedure for customizing template files for use in your own personalized template is to make a copy of the corresponding file from `template_default`, put it into your own template folder (and matching folder structure), and make your customizations in that copy of the file.

This way the only files you need in your personalized template folder are those that you have altered in some way from `template_default`.

With that explained, it is important that whenever you upgrade your site, you should also inspect ALL the `template_default` files to determine which changes in those files need to be replicated in your customized files. Comparison/Merging Tools are essential for this process; see the [Zen Cart Developer Tools](https://docs.zen-cart.com/user/first_steps/useful_tools/) for recommendations.

The process is simple: compare the `template_default` directory files from your *old* version to the `template_default` files in the *new* version, and replicate any differences in the files in your custom/personalized template in your store. If you based your template on `responsive_classic`, you should also compare and merge any changes from that template.

Then, and only after you have done all those comparisons and updated your customized files in your custom template folder, you will copy the `template_default` files from the new version into the `template_default` directory of your store.

This way you will be left with updated personalized files *and* updated `template_default` files.

Language Files in Zen Cart 1.5.8 and above
==========================================

Upgraders from prior versions of Zen Cart will notice a signficant change to the language files in this version. Because of new stricter PHP standards, simply doing a `define` on language file constants (with multiple `define` operations being done when overrides were present) was not an approach that could be used.

Zen Cart now uses [Array based language files](/user/localization/158_language_files/). For plugins with language files which are not overridden, the older style may still be used.

If you're doing an upgrade from a pre-1.5.8 Zen Cart version and are worried about all the language file changes you'll have to figure out, there is another option. Rather than porting *all* your customizations, you may want to start small and add customizations as they are needed. Many older templates made unnecessary changes which you will not want to carry forward. See [basic language file customizations](https://docs.zen-cart.com/user/localization/basic_158_language_customizations/) for a minimal starting list.

For developers with language skills who would like to build a new translation, [developer information on Array based language files](/dev/languages/158_language_files/) is provided.


## 2.2.0 
The improvements in v2.2.0 include:  
- TBD

---

{{% release_footer %}}
