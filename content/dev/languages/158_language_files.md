---
title: Developer Information on Array based Language files
description: Structure of Language Packs for Zen Cart 1.5.8 and above 
weight: 100 
layout: docs
---

In Zen Cart 1.5.8, the language file structure was modified so that the PHP `define` statement is no longer used directly to set a language constant.  The reason for this is that newer versions of PHP will emit warning messages when a constant is redefined (in an override vs core file), so the old approach would create debug logs if something wasn't done.

The new design builds an array of language definitions which are built into constants once all of them are read.  For this reason, the new files are called *array based language files* (as opposed to the older *define based language files*). 

So for example, in Zen Cart 1.5.7, the file `includes/languages/english/login.php` would have: 

```
define('HEADING_TITLE', 'Welcome, Please Sign In');
```

In Zen Cart 1.5.8, the file `includes/languages/english/lang.login.php` would have: 

```
$define = [
...
    'HEADING_TITLE' => 'Welcome, Please Sign In',
... ]; 

```

with a `define` to be done later after all the strings had been gathered.

Using arrays allows for the following kinds of behavior: 

- Create a set of language definitions in the storefront override files, but run the base file to ensure that any missing definitions are created, while not updating any definitions that are changed in the override.

- Create a definition in the main language file which works for most cases, but allow it to be overridden in a per-page language file. 

In the process of doing this work, the language files were reviewed for duplicates, and consolidation was done where appropriate to reduce the burden on translators. 

Developers seeking to build new translations for 1.5.8 and above have two options: 

1. Start with the English files, and do the translations by hand.  The advantage of this approach is that it is just translation; all the necessary code changes in each language file have been done. 

2. Start with an older translation, and run the [Language File Converter](https://github.com/torvista/Zen_Cart-Language_File_Converter). This reduces the translation burden, but requires coding skills, since the produced files will need to be hand edited in cases where the tool didn't produce perfect results. 

Of course, a hybrid approach is possible where (2) is performed, and then issues are resolved on a per-file basis using approach (1). 

### Issues with the Converter 

The Converter is not perfect.  It allows rapid conversion of language files, but some portion of the output will still need manual correction.  Translators following approach (2) above will need to make changes in the following situations: 

- references to global variables such as `$template` (example: `credit_cards.php`) 

- separate code paths for admin vs storefront (example: `square.php`)

- backward references to language definitions from earlier within the same file (example: `shopping_cart.php` reference to `TEXT_CART_HELP`)

- Parameterized calls to `zen_href_link` (example: `checkout_success.php`)

- PHP statements in isolation (example: `setlocale` in `english.php`)

- checks for `if (!defined(` (example: `paypalwpp.php`)

- links to javascript functions (example: `shopping_cart.php` definition for `TEXT_CART_HELP`)

- definitions which begin with a constant (example: `gv_faq.php` definition for `NAVBAR_TITLE`)
 
Referring to the `english` translation will demonstrate a known-working approach for fixing these issues. 

One common failure the converter has is failing to change a comma to a double arrow operator in a `define`.  For example, changing 

`define('TEXT_ONETIME_CHARGES_EMAIL',"\t" . '*onetime charges = ');`

to 

`'TEXT_ONETIME_CHARGES_EMAIL', "\t" . '*onetime charges = ',`

These failures can be detected with this grep pattern: 

```
grep "'[A-Z0-9_]*'[\s]*," *.php | grep -v "=>"
```

### Available Array Based Language Packs for Zen Cart 1.5.8 and above

Please see [User information on Array based Language files](/user/localization/158_language_files/). 

## Code Conversion 

If you need to include a language file directly, see the code example in the [Upgrading plugins for 1.5.8](/dev/plugins/upgrading_to_158/#array-based-language-files) FAQ.

