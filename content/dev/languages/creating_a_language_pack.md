---
title: Creating a Language Pack 
description: Creating an array based language pack
weight: 100 
layout: docs
---

This documentation is for Zen Cart 1.5.8 and above; if you need the older documentation, please see [Pre 1.5.8 Language Files](/dev/languages/pre_158/).

If you are not familiar with the new language file format for Zen Cart 1.5.8 and above, please see [Developer Information on Array based Language files](/dev/code/158_language_files/). 

<hr>

If you're multilingual, we'd love to have your help building new language packs.  We have [a few updated language packs](/user/localization/updated_language_packs/) but we need more. 

Developers seeking to build new translations for 1.5.8 and above have two options: 

1. Start with the English files, and do the translations by hand.  The advantage of this approach is that it is just translation; all the necessary code changes in each language file have been done. 

2. Start with an [older language pack](https://www.zen-cart.com/downloads.php?do=cat&id=6), and run the [Language File Converter](https://github.com/torvista/Zen_Cart-Language_File_Converter). This reduces the translation burden, but requires coding skills, since the produced files will need to be hand edited in cases where the tool didn't produce perfect results. 

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

{{% language_help_links %}}
