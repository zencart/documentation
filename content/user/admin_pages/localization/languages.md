---
title: Languages
category: admin_pages
weight: 20
---

This page allows you to add additional language(s) in order to internationalize the output generated by Zen Cart.

## New Language

To add a new language, click on the _new language_ button. A form will appear. Enter the information, then click on the _insert_ button to add the new language. Click on the _cancel_ button if you change your mind.

Adding the new language also makes the following database changes: 
- populates the `orders_status` table with order statuses in the *current* language.  Go to Admin > Localization > Orders Status and update them to the new language. 
- if [POSM](/user/running/posm/) is installed, populates the `products_options_stock_names` table in the current language.  Go to Localization >Out-of-Stock Labels and update them to the new language.


### Name

This is the name of the language, probably best as expressed _in itself_, e.g. Francais for French, Español for Spanish, Deutsch for German, etc.

### Code

This is the two-letter ISO 639 language code, e.g. en for English, fr for Francais, es for Español, etc. If you don't know the code, you can find it on Wikipedia [here](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes). In the rare case that you need to localize languages you can use [localization tags](https://www.ietf.org/rfc/bcp/bcp47.txt) (`en_GB` instead of `en`) but you will need to install each as separate languages.

### Image

This would be a small icon used to identify the language. This would most likely be a gif image of the typical flag for some country commonly associated with that language. This should be located in the `/includes/languages/YOURLANGUAGE/images` folder.

### Directory

This directory is where the translated PHP source files for this language are contained. For example, enter '*english*' the directory for the English language is located at 
`/includes/languages/english`. 

### Sort order

This is the order that the languages are to appear in. Lower numbers are shown higher on the screen.

### Set as default

Check this box if this is the default language for this site.

When you finish entering data, click on the _insert_ button to add the new language. Click on the _cancel_ button to discard this form.

If you have not yet [installed the language pack's files](#installing-a-language-pack) you will see the warning message 

     MISSING LANGUAGE FILES OR DIRECTORIES ... YOURLANGUAGE YOURLANGUAGE

## Edit Language

If you need to change the information about an existing language, click on the named language so that the right arrow appears in the Action column, then click on the _edit_ button. The fields on the screen are the same for adding a language. When finished editing, click on the _update_ button to save the changes, or click on _cancel_ to discard them.

## Delete Language

To remove a language, click on the named language so that the right arrow appears in the Action column, then click on the _Delete_ button. If this is not the default language, you will be asked to confirm. Click on the _delete_ button again to delete the language, or _cancel_ if you do not wish to delete this language. If this is the default language, only the _cancel_ button will appear, as you cannot delete the default language.

## Installing A Language Pack's Files 

You can create a multi-language store by copying a language pack fileset to your cart and then using the Zen Cart admin to add the new Language as described above. 

Language packs may be found in the [Plugins Library](https://www.zen-cart.com/downloads.php?do=cat&id=6).

Language packs are structured to correspond to your cart folders, so you can just 
rename the admin folder, if one exists, and then upload all the files. 

If you're not familiar with installing a Zen Cart plugin, follow the instructions on [how to install a plugin](/user/plugins/how_to_install_a_plugin/). 

{{% language_help_links %}}
