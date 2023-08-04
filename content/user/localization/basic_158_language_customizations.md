---
title: Basic 158+ Language Customizations
description: Starting from scratch for 1.5.8 with language files
category: localization
weight: 10
---

In Zen Cart 1.5.8, the language file system was reworked because of changes in PHP8.  (You can read more about the new [Array based language files](/dev/code/158_language_files/) if you want background information on this change.) 

If your pre-158 cart has a large number of language file overrides, it may be easier for you to just start fresh with the 1.5.8 language files and apply a minimal set of customizations.  Use the following tables as a guide.

Note: You will still want your [define page](/user/template/define_pages/#define_page_files) customizations from `includes/languages/english/html_includes/YOURTEMPLATE`, which you can use as-is.

# Admin Side 

## Files in admin/includes/languages 

|File|Defines|
|----|-------|
|`lang.english.php`|`HEADER_ALT_TEXT, HEADER_LOGO_IMAGE, HEADER_LOGO_WIDTH, HEADER_LOGO_HEIGHT` |

## Files in admin/includes/languages/english

|File|Defines|
|----|-------|
|`lang.email_extras.php`|`EMAIL_LOGO_ALT_TITLE_TEXT, EMAIL_LOGO_FILENAME, EMAIL_LOGO_WIDTH, EMAIL_LOGO_HEIGHT`| 


# Storefront side 

## Files in includes/languages/english/YOURTEMPLATE

|File|Defines|
|----|-------|
|`lang.email_extras.php`|`EMAIL_LOGO_ALT_TITLE_TEXT, EMAIL_LOGO_FILENAME, EMAIL_LOGO_WIDTH, EMAIL_LOGO_HEIGHT`| 
|`lang.header.php`|`HEADER_ALT_TEXT, HEADER_LOGO_IMAGE, HEADER_LOGO_WIDTH, HEADER_LOGO_HEIGHT, HEADER_SALES_TEXT`|
|`lang.meta_tags.php`|`TITLE, SITE_TAGLINE, CUSTOM_KEYWORDS `|
|`lang.index.php`|`HEADING_TITLE, HEADING_TITLE_NESTED`|

## Modifications in an Override File 

If you want to add some custom definitions, say to lang.english.php, there are a couple of workable options.  These are additions you would make to the bottom of the file before the `return` statement.

- You can add them one at a time to the `$define` array: 

```
  $define['MY_NEW_ENTRY'] = 'My entry value'; 
```

- Or, you can append them to the original array directly: 

```
  $define += [
     'MY_NEW_ENTRY' => 'My entry value', 
  ]; 
```

- Or, you can add them to a new array, and append that array to the original one.

```
  $new_defines = [
     'MY_NEW_ENTRY' => 'My entry value', 
     'MY_NEW_ENTRY_2' => 'My entry value 2', 
  ]; 
  $define += $new_defines; 
```

If you need to reference entries in the original list, just remember that they are not yet `defined` values as in prior releases; you have to reference them as array entries. 

```
$define['FEATURED'] = '<li><a href="' . zen_href_link(FILENAME_FEATURED_PRODUCTS) . '">' .  $define['TABLE_HEADING_FEATURED_PRODUCTS'] .  '</a></li>';
```

Notice that the anchor text is `$define['TABLE_HEADING_FEATURED_PRODUCTS']` rather than `TABLE_HEADING_FEATURED_PRODUCTS`.

You can read more about array based language files in [Language Files - Developer Information on Array based Language files](/dev/code/158_language_files/). 

{{% language_help_links %}}
