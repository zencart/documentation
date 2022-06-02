---
title: Release Specific Upgrade Considerations 
description: Watch for these changes if you are upgrading and preserving customizations
category: Upgrading
weight: 10
---

This document lists things you may wish to take into account as you upgrade.  This includes: 

- changes to the database schema or contents which deserve special notice
- changes to basic template operation 

**Note:** Please be sure to also check [Template Changes](/user/template/template_changes/).

### ALL Versions 

- Part of staying up to date is monitoring not just your Zen Cart version, but all your other software dependencies, such as JavaScript.  Use a tool like Google Chrome Lighthouse to [find outdated JavaScript libraries with known vulnerabilities](/user/upgrading/javascript_updates/). 

- Part of keeping modern is embracing newer PHP versions. You will need to address various [common issues with PHP version incompatibility](/user/upgrading/php_warnings/).

- Be sure external links are constructed with `rel="noreferrer noopener"`.

- If you use a custom template, check it against [the template changes list](/user/template/template_changes/). 

### Zen Cart 1.5.8 (currently in development phase, not released yet)

- Most "functions" (both admin and non-admin) have been consolidated into files located in `/includes/functions/`. Some have been merged together. Some changes are listed below.

- Language file inclusions must be changed to comply with the new language file format.  See [Developer Information on Array based Language files](/dev//languages/158_language_files/) for more details. 

- The function `zen_parse_search_string` input parameters have been reversed. Plugins that use this function will require modification.

- The function `zen_get_countries` returns different array keys than previously. Admin plugins that use this function may use the new admin function `zen_get_countries_for_admin_pulldown`. 

- The function `zen_cfg_read_only` has been added.  This means any plugin authors who provided their own version of this function should remove it from their plugin (for 1.5.7+) or wrap it in `if (!function_exists('zen_cfg_read_only'))` (for older versions of Zen Cart). 

- The misspelled notifier `NOTIFIY_ORDER_CART_SUBTOTAL_CALCULATE` has been deprecated and replaced by `NOTIFY_ORDER_CART_SUBTOTAL_CALCULATE`. Code that references the misspelled notifier will continue to work (due to the [event aliasing](/dev/code/notifiers/#event-aliasing) feature), but plugins should be updated to use the corrected name.

- The constant `ROBOTS_PAGES_TO_SKIP` was previously located in the language file `meta_tags.php` despite not being language-related.   
It has been moved to its own file in `/includes/extra_configures/robots_pages_to_skip.php`.  
Plugin pages that do not require indexing (such as Back In Stock subscribe/unsubscribe) should be added to the list in the constant definition.

### Zen Cart 1.5.7 

- The configuration constant `UPLOAD_FILENAME_EXTENSIONS` was removed from the database and replaced with an entry in `includes/classes/upload.php`.   If you have modified this constant from its original setting of `jpg,jpeg,gif,png,eps,cdr,ai,pdf,tif,tiff,bmp,zip` you will want to add a custom define (in a new file) in both your `/includes/extra_configures/` and `YOUR_ADMIN/includes/extra_configures/` directories to set all the allowed extensions you want to support site-wide.

- Internal changes necessitated removing the following inclusions from `admin/includes/auto_loaders/currency_cron.core.php`: 
    - `class.base.php`
    - `init_file_db_names.php`
    - `init_database.php`

    If you have created additional cron jobs and used this file as a base, please apply the 1.5.7 changes to your custom files.

- The database field `products_description.products_viewed` has been deprecated. It will be deleted in a future release.  Product view tracking is now done using the table `count_product_views`. 

- External links have been updated to use `rel="noopener"` or `rel="noreferrer noopener"`.  If you use external links (for social networking, manufacturer sites, product URLs, etc.) you should update your template to adopt this practice. 

- The `shopping_cart` page no longer uses `TEXT_INFORMATION` from the `shopping_cart.php` language file. You will need to move the content of that define to the new `html_includes/YOURTEMPLATE/define_shopping_cart.php` page.

- A number of constants which were unused by the core were removed from language files.  If you use a plugin which relied on these defines, you should expect a PHP Notice in your `/logs` folder.   To resolve this, define the needed constants in a plugin specific file or an override, as appropriate. Some of the defines removed are `DATE_FORMAT_SHORT` and `DATE_TIME_FORMAT`, which some plugins may have used even though core Zen Cart code does not.

- The [Display Logs plugin](https://www.zen-cart.com/downloads.php?do=file&id=1583) is now built-in. If you had its files installed in prior versions, remove all those files as part of your upgrade. Then if you want to enable the plugin simply go to Admin &gt; Modules &gt; Plugins.

- The [Admin Login as Customer plugin](https://www.zen-cart.com/downloads.php?do=file&id=583), which allowed you to login on a customer's behalf, is now built-in. If you had its files installed in prior versions, remove all those files as part of your upgrade, and configure as described on the [Place Order](/user/running/login_as_customer/) help page.

- The login form built by `includes/templates/template_default/templates/tpl_login_default.php` was changed so that the `id` and `class` are both `loginForm`, rather than `login`, as in prior releases.  This is important since a direct reference to `loginForm` is made in includes/modules/pages/login/on_load_main.js.

### Zen Cart 1.5.6 

- The variable `$downloads`, returned from `includes/modules/downloads`, changed from a query result to an array.  The following template files had to be updated to accommodate this change: 

    - `tpl_modules_downloads.php`
    - `tpl_account_history_info_default.php` (possibly) 

    You will want to adjust any copies of these files in your template to process an array rather than a database query.  

- The table containing the EZ-Pages data (`ezpages`) was split into two tables, `ezpages` and `ezpages_content`.  This was done in order to add multi-language capabilities. Accordingly, any files (template overrides or custom files) which reference the `ezpages` table will need adjustment to account for this division.

- Date format updates began in this release - see [date standardization](/user/upgrading/date_standardization/). 

### Zen Cart 1.5.5

- The arguments for the notifier `NOTIFY_ORDER_AFTER_SEND_ORDER_EMAIL` were changed.  This necessitated a code change in the observers watching for it. 

- The `responsive_classic` template was introduced in this release.  If you are coming from an older release with an older template, be sure to check and verify that your template performs properly on mobile devices.  If not, you can use Responsive Classic or select another responsive template.

- Starting in this version, the email css was pulled out of the individual templates into a shared file called `email/email_common.css`.  If you are creating or updating email templates, you should follow this new practice. 

- The phpBB object was removed

### Zen Cart 1.5.2 

- The list of pages created by `includes/modules/pages/header_php.php` changed from a query result to an array.  So the template file `includes/templates/YOURTEMPLATE/templates/tpl_page_default.php` had to be updated to accommodate this change.

### Zen Cart 1.5.0 

- The admin menus are no longer built by files ending in `.dhtml`.  Instead, a new database table called `admin_pages` was introduced.  Mods which create their own menu entries must also follow this convention.  Guidelines for [upgrading plugins to 1.5](/dev/plugins/upgrading_to_1.5/) include instructions on this step.
