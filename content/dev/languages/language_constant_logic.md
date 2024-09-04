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

- If a `lang.` file exists in the same directory as a 'legacy' file (e.g. `lang.stuff.php` and `stuff.php`), the 'legacy' file ***is not loaded***, i.e. any definitions comes from the `lang.` file.
- Files in all `extra_definitions` sub-directories are loaded in alphabetical order.
- A `zc_plugin` **must** use the array-based, e.g. `lang.stuff.php`, format for any language files provided; any 'legacy' files, e.g. `stuff.php` *are ignored*.
- While a `zc_plugin` cannot override a base language file, e.g. `lang.english.php`, it _can_ override constants defined in the base file via files in its `extra_definitions` sub-directory.
- When `zc_plugins` language file(s) are loaded, each enabled plugin is checked in alphabetical order by based on its "Plugin Key" (e.g. `DisplayLogs` for the "Display logs" plugin).

## (1) Admin Language Loading

For the admin, the language constants loaded depend on:

1. The active language, e.g. `english` or `spanish`.
2. The active page, referenced as `{page-name}` in this section.
3. The presence of any language-related files in enabled `zc_plugins`.

The `/admin/includes/languages` and `/zc_plugins/plugin_key/version/admin/includes/languages` directories hold all `.php` files that provide a site's admin language constants.

### (1.1) Value-Definition Precedence

For the admin, the following precedence identifies the source of a given language-constant's value:

1. A value in a `zc_plugins`  `extra_definitions` directory; otherwise ...
2. A value in the 'base' `extra_definitions` directory; otherwise ...
3. A value in a page-specific `zc_plugins` 'base' language directory, e.g. `english/lang.{page-name}.php`; otherwise ...
4. A value in a page-specific 'base' language directory; otherwise ...
5. A value in the 'base' language-file, e.g. `lang.english.php`; otherwise ...
6. A value in a 'legacy' file (loaded from 'base' language directories only); otherwise ...
7. The constant is not defined.

### (1.2) Loading Details `TL;DR`

The actual text associated with an admin language-constant is determined by language array files' _load order_, with possible fallback to any 'english' language files. 

Once **all** the admin language arrays are loaded, language constant definitions are created for any definitions that don't already exist. The **last** value for a language-constant *overrides all previously-loaded values*!

1. The 'base' language file, e.g. `lang.english.php` is loaded.
   - If the active admin language is other than 'english', that 'base' language file, e.g. `lang.spanish.php` is loaded.
2. The language file for the current page, e.g. `english/lang.{page-name}.php`, is loaded.
   - If the active admin language is other than 'english', the language-specific file (e.g. `spanish/lang.{page-name}.php`) is loaded.
3. Any `english/lang.{page-name}.php` files found in enabled `zc_plugins` are loaded.
   - If the active admin language is other than 'english', the language-specific (e.g. `spanish/lang.{page-name}.php`) files found in enabled `zc_plugins` are loaded.
4. All `lang.*.php` files found in the `english/extra_definitions` directory are loaded in alphabetical order.
   - If the active admin language is other than 'english', all `lang.*.php` found in the language-specific directory (e.g. `spanish/extra_definitions`) are loaded in alphabetical order.
5. All `lang.*.php` files found in enabled `zc_plugins`' `english/extra_definitions` directories are loaded in alphabetical order.
   - If the active admin language is other than 'english', all `lang.*.php` files found in enabled `zc_plugins`' language-specific directories (e.g. `spanish/extra_definitions`) are loaded in alphabetical order. 

## (2) Storefront Language Loading

On the storefront, the language constants loaded depend on:

1. The active language, e.g. `english` or `spanish`.
2. The active template, referenced as `template_dir` in this section.
3. The active page, referenced as `current_page_base` in this section.
4. The presence of any language-related files in enabled `zc_plugins`.

The `/includes/languages` and `/zc_plugins/plugin_key/version/catalog/includes/languages` directories hold all `.php` files that provide a site's storefront language constants.

### (2.1) Storefront Global Language Constants

These constants are of two types:

1. The "base" language constants.
2. Extra language-constant definitions.

#### (2.1.1) Value-Definition Precedence

Storefront 'global' language-constants are defined using this basic precedence:

1. A value in an extra-definitions template-override directory, e.g. `/english/extra_definitions/template_dir/lang.stuff.php`; otherwise ...
2. A value in a `zc_plugins` `extra_definitions` directory; otherwise ...
3. A value in a 'base' extra-definitions directory, e.g. `/english/extra_definitions/lang.stuff.php`; otherwise ...
4. A value in an additional 'base' language files (see **2.1.2** for the names of those files); otherwise ...
5. A value in the 'base' language file, e.g. `lang.english.php`; otherwise ...
6. A value in a 'legacy' language file (loaded in the same order as above); otherwise ...
7. The language constant is not defined.

#### (2.1.2) Loading Details (`TL;DR`)

***Notes***:

- For a given language-constant, the last value loaded is what is used as the constant's value.
- Any file specifically named, e.g. `/includes/languages/template_dir/lang.english.php`, is loaded only if present.
- In the lists that follow, any `english` language file(s) that do not have a <sup>superscripted</sup> note **are always loaded**.

For the loading descriptions that follow, let's pretend that a site is dual-language, supporting `english` and `spanish`.

***Loading Notes***:

<sup>1</sup> Loaded only if the current customer language is `spanish`.

<sup>2</sup> Loaded only if the current customer language is `english`.

<sup>3</sup> Prior to zc210, a constant found in a `zc_plugin`'s `extra_definitions` directory could not be overridden on the storefront.  See [this Zen Cart PR](https://github.com/zencart/zencart/pull/6493) for details.

##### (2.1.2.1) Load Array Language Files

The storefront global (i.e. for every page) array-based language files are loaded in this order:

1. Load `/includes/languages/lang.english.php`
2. Load `/includes/languages/lang.spanish.php`<sup>1</sup>
3. Load `/includes/languages/template_dir/lang.english.php`<sup>2</sup>
4. Load `/includes/languages/template_dir/lang.spanish.php`<sup>1</sup>
5. Each of the additional base language files (`lang.email_extras.php`, `lang.header.php`, `lang.button_names.php`, `lang.icon_names.php`, `lang.other_image_names.php`, `lang.credit_cards.php`, `lang.whos_online.php` and `lang.meta_tags.php`) are loaded in the order specified, looking in the following directories:
   1. Load `/includes/languages/english/filename.php`
   2. Load `/includes/languages/english/template_dir/filename.php`<sup>2</sup>
   3. Load `/includes/languages/spanish/filename.php`<sup>1</sup>
   4. Load `/includes/languages/spanish/template_dir/filename.php`<sup>1</sup>
6. Load all `lang.*.php` files found in `/includes/languages/english/extra_definitions`
7. Load all `lang.*.php` files found in any zc_plugins’  `/catalog/includes/languages/english/extra_definitions`<sup>3</sup>
8. Load all `lang.*.php` files found in any zc_plugins’  `/catalog/includes/languages/english/extra_definitions/default`<sup>3</sup>
9. Load all `lang.*.php` files in `/includes/languages/english/extra_definitions/template_dir`<sup>2</sup>
10. Load all `lang.*.php` files found in `/includes/languages/spanish/extra_definitions`<sup>1</sup>
11. Load all `lang.*.php` files found in any zc_plugins’  `/catalog/includes/languages/spanish/extra_definitions`<sup>1, 3</sup>
12. Load all `lang.*.php` files found in any zc_plugins’ `/catalog/includes/languages/spanish/extra_definitions/default`<sup>1, 3</sup>
13. Load all `lang.*.php` files in `/includes/languages/spanish/extra_definitions/template_dir` <sup>1</sup>

##### (2.1.2.2) Load 'legacy' Language Files

Once all the array-based files have been loaded, 'legacy' language files (which specify their language constants via PHP `define` statements) are loaded.

***Notes***:

1. If a `lang.` file exists in the same directory as a 'legacy' file (e.g. `lang.stuff.php` and `stuff.php`), **the 'legacy' file *is not loaded***, i.e. all definitions come from the `lang.` file!
2. 'Legacy' language files are not supported for zc_plugins!
3. Any language-constant duplication in these loaded files will result in a PHP Warning when running on PHP 8.0 and later!

The storefront global (i.e. for every page) file-based language files are loaded in this order:

1. Load `/includes/languages/spanish.php`<sup>1</sup>
2. Load `/includes/languages/template_dir/english.php`<sup>2</sup>
3. Load `/includes/languages/template_dir/spanish.php`<sup>1</sup>
4. Each of the additional base language files (`email_extras.php`, `header.php`, `button_names.php`, `icon_names.php`, `other_image_names.php`, `credit_cards.php`, `whos_online.php` and `meta_tags.php`) are loaded in the order specified, looking in the following directories:
   1. Load `/includes/languages/english/template_dir/filename.php`<sup>2</sup>
   2. Load `/includes/languages/spanish/filename.php`<sup>1</sup>
   3. Load `/includes/languages/spanish/template_dir/filename.php`<sup>1</sup>
5. Load all `*.php` files *whose names do not begin with* `lang.` found in `/includes/languages/english/extra_definitions`
6. Load all`*.php` files *whose names do not begin with* `lang.`  in `/includes/languages/english/extra_definitions/template_dir`<sup>2</sup>
7. Load all `*.php` files *whose names do not begin with* `lang.`  found in `/includes/languages/spanish/extra_definitions`<sup>1</sup>
8. Load all`*.php` files *whose names do not begin with* `lang.`  in `/includes/languages/spanish/extra_definitions/template_dir` <sup>1</sup>

##### (2.1.2.3) Make Language Constants

Now that all the 'legacy' language files have been loaded, all array-based language-constants are created via a PHP `define` statement &mdash; so long as the associated language-constant is not already defined.

### (2.2) Storefront Page-Specific Language Constants

These constants are _specific_ to the page being loaded, as recorded in `$current_page_base`.  These language constants are loaded in a *different manner* than the global ones.

The _difference_ in loading is to mimic the pre-zc158 'legacy' language-loading.  For the `account` page, for instance, the`account.php`, file would be loaded, following by *all other language files* named `account*.php` &mdash; including the 'core' `account_edit.php` (and others) as well as extra page-specific files, e.g. `account_something.php`.

#### (2.2.1) Value-Definition Precedence

Storefront page-specific language-constants are defined using this *basic* precedence; see **2.2.2** for details:

1. Load the 'base' page-specific array file, e.g. `lang.{page-name}.php`:
   1. If found in the 'base' template-override directory, e.g. `english/template_dir/lang.{page-name}.php`, use that; otherwise ...
   2. If found in a `zc_plugins` directory, use that; otherwise ...
   3. If found in the 'base' directory, e.g. `english/lang.{page-name}.php`, use that.
   4. Create any constants found in the above directories.
2. Load any page-extensions array files.  These files match the pattern `lang.{page-name}*.php`, where the file's name is not the 'base' page-specific file.  These files are loaded and constants created as described above.
3. Load any 'legacy' language files found, e.g. `{page-name}.php`:
   1. Load the file from the 'base' template-override directory.
   2. Load the file from the 'base' directory.
4. Load any 'legacy' page-extensions files:
   1. Load files from the 'base' template-override directory.
   2. Load files from the 'base' directory.

#### (2.2.2) Loading Details (`TL;DR`)

Let's pretend that a site is dual-language, supporting `english` and `spanish`, and we're loading files for the `{page-name}` page.

***Notes***:

- Language-constant values specified in these files *do not override any constants previously identified in the storefront's global language files*!
- Any file specifically named, e.g. `/includes/languages/english/lang.{page-name}.php`, is loaded only if present.
- In the list that follows, any `english` language file(s) that do not have a <sup>superscripted</sup> note **are always loaded**.

***Loading Notes***:

<sup>1</sup> Loaded only if the current customer language is `spanish`.

<sup>2</sup> Loaded only if the current customer language is `english`.

##### (2.2.2.1) Load 'base' Array Language Files

The 'base' language array-file(s) for the current page are loaded and constants created based on the current language and template.

1. Load `/includes/languages/english/lang.{page-name}.php`
2. Load `/includes/languages/spanish/lang.{page-name}.php`<sup>1</sup>
3. Load all `lang.{page-name}.php` files found in any zc_plugins’  `/catalog/includes/languages/english`
4. Load all `lang.{page-name}.php` files found in any zc_plugins’  `/catalog/includes/languages/spanish`<sup>1</sup>
5. Load all `lang.{page-name}.php` files found in any zc_plugins’  `/catalog/includes/languages/english/default`
6. Load all `lang.{page-name}.php` files found in any zc_plugins’  `/catalog/includes/languages/spanish/default`<sup>1</sup>
7. Load `/includes/languages/english/template_dir/lang.{page-name}.php`<sup>2</sup>
8. Load `/includes/languages/spanish/template_dir/lang.{page-name}.php`<sup>1</sup>

Once all these array-based language files are loaded, `define` the associated constants (if not already defined).

##### (2.2.2.2) Load Array Language File 'Extensions'

Next, any page-extension language array-files for the current page are loaded alphabetically and constants created. A page-extension file is named `lang.{page-name}*.php`, *where the file is not specifically named* `lang.{page-name}.php`. These files are loaded *in alphabetical order* from each of the directories listed below.

This processing enables _additional_ constants to be defined for a given 'page' &mdash; for example, `lang.{page-name}_something.php`.

1. Load all `lang.{page-name}*.php` files found in  `/includes/languages/english`
2. Load all `lang.{page-name}*.php` files found in `/includes/languages/spanish`<sup>1</sup>
3. Load all `lang.{page-name}*.php` files found in any zc_plugins’  `/catalog/includes/languages/english`
4. Load all `lang.{page-name}*.php` files found in any zc_plugins’  `/catalog/includes/languages/spanish`<sup>1</sup>
5. Load all `lang.{page-name}*.php` files found in any zc_plugins’  `/catalog/includes/languages/english/default`
6. Load all `lang.{page-name}*.php` files found in any zc_plugins’  `/catalog/includes/languages/spanish/default`<sup>1</sup>
7. Load all `lang.{page-name}*.php` files found in `/includes/languages/english/template_dir`<sup>2</sup>
8. Load all `lang.{page-name}*.php` files found in `/includes/languages/spanish/template_dir`<sup>1</sup>

Once all these array-based language files are loaded, `define` the associated constants (if not already defined).

##### (2.2.2.3) Load 'legacy' Language Files

Once all the array-based page-specific files have been loaded and their constants defined, 'legacy' language files (which specify their language constants via PHP `define` statements) are loaded.

***Notes***:

1. If a `lang.` file exists in the same directory as a 'legacy' file (e.g. `lang.{page-name}.php` and `{page-name}.php`), **the 'legacy' file *is not loaded***, i.e. all definitions come from the `lang.` file!
2. 'Legacy' language files are not supported for zc_plugins!
3. Any language-constant duplication in these loaded files will result in a PHP Warning when running on PHP 8.0 and later!
4. A page-extension file is named `{page-name}*.php`, *where the file is not specifically named* `{page-name}.php`. These files are loaded *in alphabetical order* from each of the directories listed below.

The storefront page-specific 'legacy' language files are loaded in this order:

1. Load `/includes/languages/spanish/template_dir/{page-name}.php`<sup>1</sup>
2. Load `/includes/languages/spanish/{page-name}.php`<sup>1</sup>
3. Load `/includes/languages/english/template_dir/{page-name}.php`<sup>2</sup>
4. Load `/includes/languages/english/{page-name}.php`
5. Load all `{page-name}*.php` files found in `/includes/languages/spanish/template_dir`<sup>1</sup>
6. Load all `{page-name}*.php` files found in `/includes/languages/spanish`<sup>1</sup>
7. Load all `{page-name}*.php` files found in `/includes/languages/english/template_dir`<sup>2</sup>
8. Load all `{page-name}*.php` files found in `/includes/languages/english`
