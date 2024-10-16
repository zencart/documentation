---
title: What's New in Version 2.1.0
description: Features and fixes in Zen Cart 2.1.0
category: release
weight: 100
layout: docs
noindex: yes
---

{{% construction %}}

{{% release_welcome %}}

About PHP versions
==================

Zen Cart v2.1.x is designed for PHP 8.0 to 8.3, with MySQL 5.7.8+ (or MariaDB 10.2.7+) and Apache 2.2/2.4.

Upgrade Instructions
====================

See the [online docs](/user/upgrading/) for upgrading advice, including Release-Specific considerations to note regarding this version. 
  
This document only mentions the actual changes specific to v2.1.x since v2.0.1.

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

For a list of files that have been changed since v2.0.1, see the [changed_files-v2.1.0](/release/changed_files-v2-1-0/) document.

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


## 2.1.0 
The improvements in v2.1.0 include:  
- **New Feature:** The [Products Options Stock Manager](https://vinosdefrutastropicales.com/product_extra_files/options_stock/readme.html) plugin (sometimes called POSM) is integrated with Zen Cart as an encapsulated plugin. This feature will help storeowners who have product variants whose stock needs to be tracked (red large t-shirts vs blue medium t-shirts, for example). It is designed as an alternative to the various “Stock by Attributes” plugins which are currently in use. See [Variant Stock](/user/running/posm/) for more details.
- New Feature: shipping/payment/order-total modules may now be delivered as [encapsulated plugins](/dev/plugins/encapsulated_plugins/).  Developers are encouraged to do so since encapsulated plugins are easier for end-users to install.  Note that any encapsulated shipping/payment/order-total modules *must* have an associated [array based language file](/dev/languages/158_language_files/).  The use of the older `define` based language files is not supported for encapsulated modules.  
- New Feature: Categories may now be featured.  (Prior releases only allowed featuring individual products.)  See [Featured Categories](/user/admin_pages/catalog/featured_categories/) for details.
- New Feature: The Zen Cart admin may now be secured with [Multi Factor Authentication](/user/security/multifactor/). 
- New Feature: [Layout Boxes Controller](/admin_pages/tools/layout_boxes_controller/) made more user friendly. 
- New Feature: Templates may now have a separate list of links for  their mobile menus.  (In prior releases, the mobile menu would reuse the desktop header link list.)  See [this PR](https://github.com/zencart/zencart/pull/6697) for details.
- Admin: The plugin formerly known as [Mod List](https://www.zen-cart.com/downloads.php?do=file&id=2039) is now included in the core and named "System Inspection."  It is an [encapsulated plugin](/dev/plugins/encapsulated_plugins/), so it can be installed using Admin > Modules > Plugin Manager.
- Admin: Manufacturer Part Number (MPN) field added in Zen Cart 2.0.0 can now be edited in the admin. 
- Admin: Manufacturer Part Number (MPN) field is now included in the admin search list of fields to be checked.
- Admin: The UI for the Plugin Manager has been re-arranged for easier viewing.
- Admin: UI has better multi-language support.  See [Admin Language conversion](/dev/languages/admin_language_translation/).
- Admin: FIXED - Search in Options Values Manager.
- Admin: FIXED - Salemaker sales with be enabled/disabled by clicking the status icon.
- Admin: FIXED - Sales Report with Graphs monthly pagination now works; dates in legend no longer truncated.
- Admin: FIXED - CKEditor security warning fix is built-in.
- Admin: FIXED - Enabling and disabling sales by clicking icon works. 
- Admin: FIXED - Viewing customer records would occasionally lead to a blank right hand infoBox.
- Admin: FIXED - Viewing orders would occasionally lead to a blank right hand infoBox.
- Admin: FIXED - Selecting coupons on pages other than the first page would occasionally fail.
- Admin: The <a href="/dev/code/template_settings/">template settings file</a> may now be viewed from your admin page.
- Admin: The date of last password change is now shown on the Users page in admin.
- Admin: Product Price fields "Gross" and "Net" have been renamed to "Tax Included" and "Tax Excluded."
- Core: For robustness, in multi-language stores, missing non-English language constants will now fall back to their English definitions.
- Core: Add parameter to Customer class notifier to allow data to be added to class.
- Core: Retired Notifiers and Observers can be set to generate deprecated logs automatically.
- Core: Zones module now has exception rules notifier.  See <a href="/user/shipping/exceptions/">this page</a> for details on usage.
- Core: Many improvements in multi-language handling.
- Extras: Improved and modernized utilities in the `/extras` folder.
- Installer: `zc_install` now uses Bootstrap 5.  Zurb Foundation is no longer used.  UI greatly improved. 
- Modernization: A `Product` class has been introduced to encapsulate product-specific logic.
- Modernization: Shipping modules now inherit from the `ZenShipping` base class to reduce code duplication and ensure consistency.
- Storefront: `tpl_{product-type-page}_display.php` files have been consolidated to reduce code duplication.
- Storefront: FIXED - Second Place Order done from admin before completing first one works as expected.
- Storefront: FIXED attribute pricing display issues.
- Storefront: FIXED fractional product quantities handling.
- Storefront: Gift Certificate FAQ page layout improvements.
- Storefront: Additional image matching rules now are enforced more strictly for new installs; see [this page](/user/images/additional_images/#additional-images-filename-matching-rules) for details.  

---

{{% release_footer %}}
