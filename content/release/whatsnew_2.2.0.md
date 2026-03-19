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

Zen Cart v2.2.x is designed for PHP 8.2 to 8.4, with MySQL 5.7.8+ (or MariaDB 10.2.7+) and Apache 2.2/2.4.

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

The improvements in v2.2.0 include the following.  The changes which are most notable are bolded.

- **Admin: Order statuses are now color coded.** See [Orders Status](/user/admin_pages/localization/orders_status#color-coding).  This change makes the [Admin > Orders](/user/admin_pages/customers/orders#colors) screen easier to scan. 
- Admin: Permit the saving of configuration values as HTML character codes.
- Admin: Updates to System Inspection plugin.
- **Admin: Additional images may now be specified in the database rather than using the older [filename matching mechanism](/user/images/image_filename_conventions/).  See [Additional Images Handling](/user/images/additional_images_database/) for details.**
- Admin: Customers page now has a legend explaining the icons used in the Authorized column.
- Admin: A sample cron job is provided for storeowners who wish to enable upcoming products at a specific time.  See [Cron Jobs within Zen Cart](/dev/code/admin_cron/#existing-cron-jobs-within-zen-cart).
- **Admin: [Customer account activation](/user/orders/customer_approval/#customer-account-activation) for customer accounts added.  Stores may now require that new accounts authenticate their email addresses for fraud control.**
- Admin: The page Admins > Admin Page Registration has been removed.
- **Admin: Configuration screen now allows all values in a group to be updated at once.  See [Configuration in Zen Cart 2.2.x](/user/admin_pages/configuration/v2.2.0/).**
- Admin: Fixed - Payment modules with Zone restrictions could falsely show message "The configuration of the order's payment module has changed."
- Admin: Fixed - Undefined constant error in `includes/functions/functions_exchange_rates.php`.
- Admin: Payment, Shipping and Order Total Modules now grouped by status and sort order. 
- Admin: Plugin Manager Modules now grouped by status and sort order. 
- Admin: Fixed - Banner manager crashes when no image provided on update.
- Admin: Improvements in Sales Report with Graphs.
- Admin: TinyMCE added as the default admin  [HTML Editor](/user/running/html_editors). (CKEditor is locked at an older version; no updates planned.)
- Admin: Added capability to customize the upper right link bar using a notifier. 
- Admin: Fixed - Deprecated "Passing null to parameter #1" log created when viewing Admin Packingslip or Admin Invoice.
- Core: We are simplifying the distribution by removing Laravel.
- Core: Improved handling of `product` table records which do not have associated `products_description` records.
- The `DB_CHARSET` setting in the `dist-configure.php` files (Storefront and Admin) has been updated to `utf8mb4`, which is the character set your database should be using at this point.  If it isn't, see [Converting to UTF8MB4](/user/upgrading/convert_to_utf8/) for instructions.
- **Core: PayPal RESTful pulled in to core.  This updated integration is intended to replace the older PayPal integrations, which will be deprecated at some point in the future by PayPal.  All Zen Cart users are encouraged to upgrade.  For more information, see [PayPal RESTful](/user/payment/paypal_restful/).**
- Core: Improved PHP 8.4 compatibility. Note that plugins may require updating to run without warnings under PHP 8.4. 
- Core: Typo in notifier name `NOTIFY_ADMIN_INVOICE_HEADERS_AFTER_TAX` corrected.
- Core: Updates to POSM to support [Edit Orders 5.0](https://www.zen-cart.com/downloads.php?do=file&id=2400).
- Core: Correct PHP warnings when added product isn't POSM-managed 
- **Core: Password reset via URL (versus emailing a temporary password) is being added to the core.  Credit to forum users Numinix and Retched for inspiration.**
- Core: Improvements for International use.
- Extras: Curltester now includes REST API endpoints for USPS and PayPal. 
- Storefront: Wholesale customers are shown a header message acknowledging their wholesale status.
- Storefront: Tax descriptions may now be multilingual.
- Storefront: Password forgotten now disallowed for banned email addresses.
- Storefront: Correct `get_template_dir` loading behavior for CSS, JS and PHP.
- Storefront: Notifier added for additional product details.
- Storefront: Updated embedded MobileDetect to latest version for `responsive_classic` template.
- **Storefront: Updated - Refreshed look for responsive classic template.  See [this repo from contributor chadlly2003](https://github.com/chadlly2003/zencart_responsive_classic_redesign), and [the Responsive Classic Redesign help file](/user/template/responsive_classic_redesign/).**
- Storefront: Fixed - Customer's wholesale status captured when order is placed.
- Storefront: Fixed - PHP log created when empty shipping quote returned.
- Storefront: Fixed - JavaScript problems can occur when `gv_balance` is null. This is an important fix for JavaScript heavy checkouts (OPC, some payment modules).

---

{{% release_footer %}}
