---
title: What's Next for Zen Cart? 
description: Upcoming changes to Zen Cart 
category: release
weight: 100
layout: docs
noindex: yes
---

{{% construction %}}

## 3.0.0 

The improvements in v3.0.0 include the following.  The changes which are most notable are bolded.

- **New Feature: <a href="https://github.com/zencart/zencart/discussions/6428">Child Templates</a> will be supported, so that storeowners can more easily determine what has been changed from the base release of a template.**
- Modernization: Zen Cart 3.0 will use Bootstrap 5. 
- Modernization: support for older `define` based language files will be dropped.  Moving forward, only [Array based language files](/dev/languages/158_language_files/) will be supported. 

## 2.2.0 

The improvements in v2.2.0 include the following.  The changes which are most notable are bolded.

- **Admin: Order statuses are now color coded.** See [Orders Status](/user/admin_pages/localization/orders_status#color-coding).  This change makes the [Admin > Orders](/user/admin_pages/customers/orders#colors) screen easier to scan. 
- Admin: Permit the saving of configuration values as HTML character codes.
- Admin: Updates to System Inspection plugin.
- **Admin: Additional images may now be specified in the database rather than using the older [filename matching mechanism](/user/images/image_filename_conventions/).  See [Additional Images Handling](/user/images/additional_images_database/) for details.**
- Admin: Customers page now has a legend explaining the icons used in the Authorized column.
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
- Core: Improved handling of `product` table records which do not have associated `products_description` records.
- The `DB_CHARSET` setting in the `dist-configure.php` files (Storefront and Admin) has been updated to `utf8mb4`, which is the character set your database should be using at this point.  If it isn't, see [Converting to UTF8MB4](/user/upgrading/convert_to_utf8/) for instructions.
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

## 2.1.0 
Zen Cart 2.1.0 has been released; changes are now listed in [What's New in 2.1.x](/release/whatsnew_2.1.0).

## 2.0.1 
Zen Cart 2.0.1 has been released; changes are now listed in [What's New in 2.0.x](/release/whatsnew_2.0.0.html).
