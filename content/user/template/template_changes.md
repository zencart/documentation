---
title: Template Security Changes 
description: Keeping your custom template up to date.
category: template 
weight: 10 
---

## Introduction 

If you start building a new Zen Cart with the latest version, and use
the Responsive Classic template, you get all the latest fixes. 

But what if you are using another template?  How can you check to see if it
has all the most recent fixes? 

This page is intended to present a list of security fixes you will want 
to add to your template if they are not present and you have overridden the file. (If you have not overridden the file, you are using the updated copy
in `template_default`.)  You can check 
the folder `includes/templates/template_default` for the base copy of 
the specified file if you're not sure where a change should go. 

* `common/html_header.php` - use `header('X-Frame-Options:SAMEORIGIN');` to prevent clickjacking.

* `common/html_header.php` - pull in most recent versions of jQuery and other libraries.

* `common/tpl_header.php` - Use `zen_output_string_protected` for message display. 

* `sideboxes/tpl_reviews_random.php` - use `zen_output_string_protected` for review display. 

* `templates/tpl_account_default.php` - use `zen_output_string_protected` for `$orders['order_name'])` display. 

* `templates/tpl_product_info_display.php` - use `zen_output_string_protected` in `productInfoLink`. 

* `templates/tpl_product_music_info_display.php` - use `zen_output_string_protected` in `productInfoLink`. 

* `templates/tpl_product_free_shipping_info_display.php` - use `zen_output_string_protected` in `productInfoLink`. 

* `templates/tpl_account_history_info_default.php` - use `zen_output_string_protected` for output of `$_GET['order_id']`. 

