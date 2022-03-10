---
title: Template Updates 
description: Keeping your custom template up to date.
category: template 
weight: 10 
---

## Introduction 

If you start building a new Zen Cart with the latest version, and use
the Responsive Classic template (or the very well maintained [Bootstrap template](/user/template/bootstrap/)), you get all the latest fixes. 

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

