---
title: Template Updates 
description: Keeping your custom template up to date.
category: template 
weight: 10 
---

## Introduction 

If you start building a new Zen Cart with the latest version, and use
the [Responsive Classic template](/user/template/responsive_classic/) (or the very well maintained [Bootstrap template](/user/template/bootstrap/)), you get all the latest fixes. 

But what if you are using another template?  How can you check to see if it
has all the most recent fixes? 

This page is intended to present a list of security fixes and other improvements you will want 
to add to your template if they are not present and you have overridden the file. (If you have not overridden the file, you are using the updated copy
in `template_default`.)  You can check 
the folder `includes/templates/template_default` for the base copy of 
the specified file if you're not sure where a change should go. 

## Security Fixes 
* `common/html_header.php` - use `header('X-Frame-Options:SAMEORIGIN');` to prevent clickjacking.

* `common/html_header.php` - pull in most recent versions of jQuery and other libraries.

* `common/tpl_header.php` - Use `zen_output_string_protected` for message display. 

* `sideboxes/tpl_reviews_random.php` - use `zen_output_string_protected` for review display. 

* `templates/tpl_account_default.php` - use `zen_output_string_protected` for `$orders['order_name'])` display. 

* `templates/tpl_account_history_info_default.php` - use `zen_output_string_protected` for output of `$_GET['order_id']`. 

* `templates/tpl_checkout_confirmation_default.php` - use `zen_output_string_protected` for attribute value display. 

* `templates/tpl_product_info_display.php` - use `zen_output_string_protected` in `productInfoLink`. 

* `templates/tpl_product_music_info_display.php` - use `zen_output_string_protected` in `productInfoLink`. 

* `templates/tpl_product_free_shipping_info_display.php` - use `zen_output_string_protected` in `productInfoLink`. 

* `templates/tpl_product_reviews_default.php` - use `zen_output_string_protected` for review display.

* `templates/tpl_reviews_default.php` - use `zen_output_string_protected` for review display.

## Accessibility Changes

Starting in Zen Cart 1.5.6 and continuing in subsequent releases 1.5.7 and 1.5.8, significant improvements were made to both the Bootstrap and Responsive Classic templates to ensure they meet accessibility guidelines.  If you are using a custom template, you will want to perform your own [accessibility review](/user/accessibility/accessibility/).  

## Anti-Spam 

The following template files were updated in Zen Cart 1.5.7 with anti-spam features: 

* `templates/tpl_product_reviews_write_default.php`
* `templates/tpl_contact_us_default.php`
* `templates/tpl_modules_create_account.php`
* `templates/tpl_ask_a_question_default.php`

## Client side validation 

The following files were updated in Zen Cart 1.5.5 to specify a field type and required flag where needed when creating input fields:

* `templates/tpl_account_edit_default.php`
* `templates/tpl_account_password_default.php`
* `templates/tpl_contact_us_default.php`
* `templates/tpl_login_default.php`
* `templates/tpl_modules_address_book_details.php`
* `templates/tpl_modules_checkout_new_address.php`
* `templates/tpl_modules_create_account.php`
* `templates/tpl_password_forgotten_default.php`


**Note:** Please be sure to also check [Release Specific Upgrade Considerations](/user/upgrading/release_specific_upgrade_considerations/) when doing an upgrade.

## PHP Updates 

You will also want to make changes so that your older template is compliant with the latest version of PHP.  See [PHP Warnings and Deprecated messages](/user/upgrading/php_warnings/) for some common changes. 

Please note: many Zen Cart templates were written to work under PHP 5 (or even PHP 4).  You will have to do a significant amount of work to bring them up to date to work with PHP 8, which is why the [Responsive Classic template](/user/template/responsive_classic/) and [Bootstrap template](/user/template/bootstrap/) are recommended.

If you do wish to update an older template, see [Upgrading plugins to work with 1.5.8/PHP 8.0+](/dev/plugins/upgrading_to_158/) and [PHP 7 updates](/user/upgrading/php_warnings/). 

## Notifiers 
Notifiers are commonly added to each Zen Cart release.  If your custom template is using a notifier-based plugin, you will need to make sure it has all the latest notifiers. 

### Notifiers in files under `includes/templates/template_default/` 

```
./common/html_header.php:  NOTIFY_HTML_HEAD_END
./common/html_header.php: NOTIFY_HTML_HEAD_START
./common/html_header.php: NOTIFY_HTML_HEAD_TAG_START
./common/main_template_vars.php:  NOTIFY_MAIN_TEMPLATE_VARS_END
./common/main_template_vars.php:  NOTIFY_MAIN_TEMPLATE_VARS_START
./common/tpl_columnar_display.php: NOTIFY_TPL_COLUMNAR_DISPLAY_END
./common/tpl_columnar_display.php: NOTIFY_TPL_COLUMNAR_DISPLAY_START
./common/tpl_main_page.php:  NOTIFY_FOOTER_END
./common/tpl_tabular_display.php: NOTIFY_TPL_TABULAR_DISPLAY_END
./common/tpl_tabular_display.php: NOTIFY_TPL_TABULAR_DISPLAY_START
```

### Notifiers in files under `includes/modules/`

```
additional_images.php: NOTIFY_MODULES_ADDITIONAL_IMAGES_FILE_MATCH
additional_images.php: NOTIFY_MODULES_ADDITIONAL_IMAGES_GET_LARGE
additional_images.php: NOTIFY_MODULES_ADDITIONAL_IMAGES_SCRIPT_LINK
additional_images.php: NOTIFY_MODULES_ADDITIONAL_IMAGES_THUMB_SLASHES
additional_images.php: NOTIFY_MODULES_ADDITIONAL_PRODUCT_IMAGES_END
additional_images.php: NOTIFY_MODULES_ADDITIONAL_PRODUCT_IMAGES_LIST
additional_images.php: NOTIFY_MODULES_ADDITIONAL_PRODUCT_IMAGES_START
attributes.php: NOTIFY_ATTRIBUTES_MODULE_BEFORE_ASSEMBLE_OUTPUTS
attributes.php: NOTIFY_ATTRIBUTES_MODULE_CHECKBOX_SELECTED
attributes.php: NOTIFY_ATTRIBUTES_MODULE_DEFAULT_SWITCH
attributes.php: NOTIFY_ATTRIBUTES_MODULE_END
attributes.php: NOTIFY_ATTRIBUTES_MODULE_FORMAT_VALUE
attributes.php: NOTIFY_ATTRIBUTES_MODULE_OPTION_BUILT
attributes.php: NOTIFY_ATTRIBUTES_MODULE_ORIGINAL_PRICE
attributes.php: NOTIFY_ATTRIBUTES_MODULE_RADIO_SELECTED
attributes.php: NOTIFY_ATTRIBUTES_MODULE_SALEMAKER_DISPLAY_PRICE_PERCENTAGE
attributes.php: NOTIFY_ATTRIBUTES_MODULE_START_OPTION
attributes.php: NOTIFY_ATTRIBUTES_MODULE_START_OPTIONS_LOOP
category_row.php: NOTIFY_CATEGORY_ROW_IMAGE
checkout_address_book.php: NOTIFY_MODULE_END_CHECKOUT_ADDRESS_BOOK
checkout_new_address.php: NOTIFY_MODULE_CHECKOUT_ADDED_ADDRESS_BOOK_RECORD
checkout_new_address.php: NOTIFY_MODULE_CHECKOUT_NEW_ADDRESS_VALIDATION
checkout_new_address.php: NOTIFY_MODULE_END_CHECKOUT_NEW_ADDRESS
checkout_new_address.php: NOTIFY_MODULE_START_CHECKOUT_NEW_ADDRESS
checkout_process.php: NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_CREATE
checkout_process.php: NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_CREATE_ADD_PRODUCTS
checkout_process.php: NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_TOTALS_PROCESS
checkout_process.php: NOTIFY_CHECKOUT_PROCESS_AFTER_PAYMENT_MODULES_AFTER_ORDER_CREATE
checkout_process.php: NOTIFY_CHECKOUT_PROCESS_AFTER_PAYMENT_MODULES_BEFOREPROCESS
checkout_process.php: NOTIFY_CHECKOUT_PROCESS_AFTER_SEND_ORDER_EMAIL
checkout_process.php: NOTIFY_CHECKOUT_PROCESS_BEFORE_ORDER_TOTALS_PRE_CONFIRMATION_CHECK
checkout_process.php: NOTIFY_CHECKOUT_PROCESS_BEFORE_ORDER_TOTALS_PROCESS
checkout_process.php: NOTIFY_CHECKOUT_PROCESS_BEGIN
checkout_process.php: NOTIFY_CHECKOUT_PROCESS_HANDLE_AFFILIATES
checkout_process.php: NOTIFY_CHECKOUT_SLAMMING_ALERT
checkout_process.php: NOTIFY_CHECKOUT_SLAMMING_LOCKOUT
create_account.php: NOTIFY_CREATE_ACCOUNT_CAPTCHA_CHECK
create_account.php: NOTIFY_CREATE_ACCOUNT_LOOKUP_BY_EMAIL
create_account.php: NOTIFY_CREATE_ACCOUNT_VALIDATION_CHECK
create_account.php: NOTIFY_FAILURE_DURING_CREATE_ACCOUNT
create_account.php: NOTIFY_LOGIN_SUCCESS_VIA_CREATE_ACCOUNT
create_account.php: NOTIFY_MODULE_END_CREATE_ACCOUNT
create_account.php: NOTIFY_MODULE_START_CREATE_ACCOUNT
create_account.php: NOTIFY_NICK_CHECK_FOR_DUPLICATE
create_account.php: NOTIFY_NICK_CHECK_FOR_EXISTING_EMAIL
create_account.php: NOTIFY_NICK_CHECK_FOR_MIN_LENGTH
create_account.php: NOTIFY_NICK_CREATE_NEW
create_account.php: NOTIFY_NICK_SET_TEMPLATE_FLAG
create_account.php: NOTIFY_SPAM_DETECTED_DURING_CREATE_ACCOUNT
downloads.php: NOTIFY_MODULE_DOWNLOAD_TEMPLATE_DETAILS
ezpages_bar_footer.php: NOTIFY_END_EZPAGES_FOOTERBAR
ezpages_bar_footer.php: NOTIFY_START_EZPAGES_FOOTERBAR
ezpages_bar_header.php: NOTIFY_END_EZPAGES_HEADERBAR
ezpages_bar_header.php: NOTIFY_START_EZPAGES_HEADERBAR
featured_products.php: NOTIFY_MODULES_FEATURED_PRODUCTS_B4_LIST_BOX
main_product_image.php:    NOTIFY_MODULES_MAIN_PRODUCT_IMAGE_FILENAME
main_product_image.php: NOTIFY_MODULES_MAIN_PRODUCT_IMAGE_END
main_product_image.php: NOTIFY_MODULES_MAIN_PRODUCT_IMAGE_START
meta_tags.php: NOTIFY_MODULE_END_META_TAGS
meta_tags.php: NOTIFY_MODULE_META_TAGS_BUILDKEYWORDS
meta_tags.php: NOTIFY_MODULE_META_TAGS_OVERRIDE
meta_tags.php: NOTIFY_MODULE_META_TAGS_UNSPECIFIEDPAGE
meta_tags.php: NOTIFY_MODULE_START_META_TAGS
new_products.php: NOTIFY_MODULES_NEW_PRODUCTS_B4_LIST_BOX
product_listing.php: NOTIFY_MODULES_PRODUCT_LISTING_PRODUCTS_BUTTON
product_listing.php: NOTIFY_MODULE_PRODUCT_LISTING_RESULTCOUNT
product_listing.php: NOTIFY_PRODUCT_LISTING_END
product_listing_alpha_sorter.php: NOTIFY_PRODUCT_LISTING_ALPHA_SORTER_SELECTLIST
specials_index.php: NOTIFY_MODULES_SPECIALS_INDEX_B4_LIST_BOX
```

### Notifiers in files under `includes/modules/sideboxes/`
```
./ezpages.php: NOTIFY_START_EZPAGES_SIDEBOX
./ezpages.php: NOTIFY_END_EZPAGES_SIDEBOX
./ezpages.php: NOTIFY_END_EZPAGES_SIDEBOX
```

Other notifiers may have been added to non-overridable files as well; you can compare the [complete list of notifiers](/dev/code/notifiers_list/) to what you have in your files using the [Notifier Report](https://github.com/lat9/notifier_report).


