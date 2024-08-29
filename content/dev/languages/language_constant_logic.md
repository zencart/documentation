---
title: Language Constant logic 
description: How language constants are created
weight: 100 
layout: docs
---

This documentation is for Zen Cart 1.5.8 and above.  The exact behavior specified here is fully implemented in Zen Cart 2.1.0, with some minor variances in 2.0.x and 1.5.8. 

If you are not familiar with the new language file format for Zen Cart 1.5.8 and above, please see [Developer Information on Array based Language files](/dev/languages/158_language_files/). 

<hr>

# Language Constant Definition

In both the admin and the storefront environments, there are two groups of language constants:

1. Those that apply _globally_, i.e. on every loaded page.
2. Those that are _page-specific_.

The file-system sources for the associated language files is dependent on the environment (i.e. admin or storefront) in which your Zen Cart is currently running.

**Notes**:

- If a `lang.` file exists in the same directory as an un-prefixed file (e.g. `lang.stuff.php` and `stuff.php`), the un-prefixed file *is not loaded*, i.e. any definitions comes from the `lang.` file.
- While a `zc_plugin` cannot override a base language file, e.g. `lang.english.php`, it _can_ override constants defined in the base file via files in its `extra_definitions` sub-directory.
- Files in a language's `extra_definitions` sub-directory are loaded in alphabetic order.
- When `zc_plugins` language file(s) are loaded, each enabled plugin is checked in alphabetical order by based on its "Plugin Key" (e.g. `DisplayLogs` for the "Display logs" plugin).

## Admin Language Loading

For the admin, the language constants loaded depend on:

1. The active language, e.g. `english` or `spanish`.
2. The active page, referenced as `current_page` in this section.
3. The presence of any language-related files in enabled `zc_plugins`.

The `/admin/includes/languages` and `/zc_plugins/plugin_key/version/admin/includes/languages` directories hold all `.php` files that provide a site's admin language constants.

The actual text associated with an admin language-constant is determined by language array files' _load order_, with possible fallback to any 'english' language files. 

Once **all** the admin language arrays are loaded, language constant definitions are created for any definitions that don't already exist.

1. The 'base' language file, e.g. `lang.english.php` is loaded.  Language constant-definitions present in **all** other files loaded *override any previously-loaded constant-definition*!
2. If the active admin language is other than 'english', that 'base' language file, e.g. `lang.spanish.php` is loaded.
3. The language file for the current page, e.g. `english/lang.current_page.php`, is loaded.
4. If the active admin language is other than 'english', the language-specific file (e.g. `spanish/lang.current_page.php`) is loaded.
5. Any `english/lang.current_page.php` files found in enabled `zc_plugins` are loaded.
6. If the active admin language is other than 'english', the language-specific (e.g. `spanish/lang.current_page.php`) files found in enabled `zc_plugins` are loaded.
7. All `lang.*.php` files found in the `english/extra_definitions` directory are loaded in alphabetical order.
8. If the active admin language is other than 'english', all `lang.*.php` found in the language-specific directory (e.g. `spanish/extra_definitions`) are loaded in alphabetical order.
9. All `lang.*.php` files found in enabled `zc_plugins`' `english/extra_definitions` directories are loaded in alphabetical order.
10. If the active admin language is other than 'english', all `lang.*.php` files found in enabled `zc_plugins`' language-specific directories (e.g. `spanish/extra_definitions`) are loaded in alphabetical order. 

## Storefront Language Loading

On the storefront, the language constants loaded depend on:

1. The active language, e.g. `english` or `spanish`.
2. The active template, referenced as `template_dir` in this section.
3. The active page, referenced as `current_page_base` in this section.
4. The presence of any language-related files in enabled `zc_plugins`.

The `/includes/languages` and `/zc_plugins/plugin_key/version/catalog/includes/languages` directories hold all `.php` files that provide a site's storefront language constants.

### Storefront Global Language Constants

These constants are of two types:

1. The "base" language constants.
2. Extra language-constant definitions.

Let's pretend that a site is dual-language, the language currently selected by the customer is `spanish` and we're looking for the definition of `BOX_HEADING_REVIEWS`, which _should_ be present in `/includes/languages/lang.english.php`.

1. If the constant is found in a file in `/includes/languages/spanish/extra_definitions/template_dir`, it'll be used; otherwise ...
2. If the constant is found in a file in a `zc_plugin`'s `catalog/languages/spanish/extra_definitions/default`<sup>1</sup>, it'll be used; otherwise ...
3. If the constant is found in a file in a `zc_plugin`'s `catalog/languages/spanish/extra_definitions`<sup>1</sup>, it'll be used; otherwise ... 
4. If the constant is found in a file in `/includes/languages/spanish/extra_definitions`, it'll be used; otherwise ... 
5. If the constant is found in  `/includes/languages/template_dir/lang.spanish.php`, it'll be used; otherwise ... 
6. If the constant is found in  `/includes/languages/lang.spanish.php`, it'll be used; otherwise ... 
7. If the constant is found in a file in `/includes/languages/english/extra_definitions/template_dir`, it'll be used; otherwise ...
8. If the constant is found in a file in `zc_plugin`'s `catalog/languages/english/extra_definitions/default`<sup>1</sup>, it'll be used; otherwise ...
9. If the constant is found in a file in a `zc_plugin`'s `catalog/languages/english/extra_definitions`<sup>1</sup>, it'll be used; otherwise ... 
10. If the constant is found in a file in  `/includes/languages/english/extra_definitions`, it'll be used; otherwise ... 
11. If the constant is found in  `/includes/languages/template_dir/lang.english.php`, it'll be used; otherwise ... 
12. If the constant is found in  `/includes/languages/lang.english.php`, it'll be used; otherwise ... 
13. A PHP Fatal error will most likely result, due to the language constant's missing value.

Notes:

<sup>1</sup> Prior to zc210, a constant found in a `zc_plugin`'s `extra_definitions` directory could not be overridden on the storefront.  See [this Zen Cart PR](https://github.com/zencart/zencart/pull/6493) for details.

### Storefront Page-Specific Constants

These constants are _specific_ to the page being loaded, as recorded in `$current_page_base`.  These language constants are loaded in a different manner than the global ones.

Let's pretend that a site is dual-language, the language currently selected by the customer is `spanish` and we're loading files for the `shippinginfo` page.

- First, the 'base' language file(s) for the current page are loaded and constants created based on the current language and template:

1. Constants found in  `/includes/languages/spanish/template_dir/lang.shippinginfo.php` that don't already exist are created.
2. Constants found in a `zc_plugin`'s `catalog/languages/spanish/default/lang.shippinginfo.php` that don't already exist are created.
3. Constants found in a `zc_plugin`'s `catalog/languages/spanish/lang.shippinginfo.php` that don't already exist are created.
4. Constants found in `/includes/languages/spanish/lang.shippinginfo.php` that don't already exist are created.
5. Constants found in `/includes/languages/english/template_dir/lang.shippinginfo.php` that don't already exist are created.
6. Constants found in a `zc_plugin`'s `catalog/languages/english/default/lang.shippinginfo.php` that don't already exist are created.
7. Constants found in a `zc_plugin`'s `catalog/languages/english/lang.shippinginfo.php` that don't already exist are created.
8. Constants found in `/includes/languages/english/lang.shippinginfo.php` that don't already exist are created.

- Next, any page-extension language files for the current page are loaded alphabetically and constants created. 

These files match the regex pattern `'~^' . 'lang.' . $current_page_base  . '(.+)\.php$~i'`.  In "english", that means that any file named (for the current example) `shippinginfo*.php` that isn't `shippinginfo.php` &mdash; for example, `shippinginfo2.php` or `shippinginfo_something.php`.  The files are loaded in alphabetic order. For brevity, we'll refer these files simply as `shippinginfo*.php` in the ordering below.

1. Constants found in  `/includes/languages/spanish/template_dir/lang.shippinginfo*.php` that don't already exist are created.
2. Constants found in a `zc_plugin`'s `catalog/languages/spanish/default/lang.shippinginfo*.php` that don't already exist are created.
3. Constants found in a `zc_plugin`'s `catalog/languages/spanish/lang.shippinginfo*.php` that don't already exist are created.
4. Constants found in `/includes/languages/spanish/lang.shippinginfo*.php` that don't already exist are created.
5. Constants found in `/includes/languages/english/template_dir/lang.shippinginfo*.php` that don't already exist are created.
6. Constants found in a `zc_plugin`'s `catalog/languages/english/default/lang.shippinginfo*.php` that don't already exist are created.
7. Constants found in a `zc_plugin`'s `catalog/languages/english/lang.shippinginfo*.php` that don't already exist are created.
8. Constants found in `/includes/languages/english/lang.shippinginfo*.php` that don't already exist are created.

