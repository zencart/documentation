---
title: Basic 158 Language Customizations
description: Starting from scratch for 1.5.8 with language files
category: localization
weight: 10
---

If your pre-158 cart has a large number of language file overrides, it may be easier for you to just start fresh with the 1.5.8 language files and apply a minimal set of customizations.  Use the following tables as a guide.

Note: You will still want your [define page](/user/template/define_pages/#define_page_files) customizations from `includes/languages/english/html_includes/YOURTEMPLATE`, which you can use as-is.

# Admin Side 

## Files in admin/includes/languages 

|File|Defines|
|----|-------|
|`lang.english.php`|`HEADER_ALT_TEXT, HEADER_LOGO_HEIGHT, HEADER_LOGO_IMAGE, HEADER_LOGO_WIDTH` |

## Files in admin/includes/languages/english

|File|Defines|
|----|-------|
|`lang.email_extras.php`|`EMAIL_LOGO_FILENAME, EMAIL_LOGO_WIDTH, EMAIL_LOGO_HEIGHT, EMAIL_LOGO_ALT_TITLE_TEXT`| 


# Storefront side 

## Files in includes/languages/english/YOURTEMPLATE

|File|Defines|
|----|-------|
|`lang.email_extras.php`|`EMAIL_LOGO_FILENAME, EMAIL_LOGO_WIDTH, EMAIL_LOGO_HEIGHT, EMAIL_LOGO_ALT_TITLE_TEXT`| 
|`lang.header.php`|`HEADER_ALT_TEXT, HEADER_SALES_TEXT, HEADER_LOGO_WIDTH, HEADER_LOGO_HEIGHT, HEADER_LOGO_IMAGE`|
|`lang.meta_tags.php`|`TITLE, SITE_TAGLINE, CUSTOM_KEYWORDS `|

