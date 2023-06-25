---
title: Template Overrides System 
description: What's the best way to change a template? 
category: template 
weight: 5
---

Before you read this, please review 
[basic terms](/user/first_steps/basic_terms/),
[template default and default files](/user/first_steps/overrides/) and 
[overrides for new users](/user/new_user_topics/overrides/). 

## Introduction 

Overrides were created to simplify upgrading and templating. 

## What Can I Override? 

### Files under a folder with the name of your template 
Any file which exists in a folder which has a `classic` subfolder 
can be overridden by creating a folder with the name of your template, and copying the file in there. 

As of Zen Cart 1.5.6, this list is: 

```
includes/languages/
includes/languages/english/extra_definitions/
includes/languages/english/
includes/languages/english/html_includes/
includes/languages/english/modules/payment/
includes/languages/english/modules/shipping/
includes/languages/english/modules/order_total/
includes/modules/
includes/modules/sideboxes/
```

In addition, you can override: 

```
includes/index_filters/ 
```

As an example of this, if your template is called `bootstrap`, then to override `includes/modules/category_row.php`, you would create `includes/modules/bootstrap/category_row.php`.


You can also override any folder in your template folder.
Again as of 1.5.6, this list is: 

```
YOUR_TEMPLATE/buttons/
YOUR_TEMPLATE/common/
YOUR_TEMPLATE/css/
YOUR_TEMPLATE/images/
YOUR_TEMPLATE/info_shopping_cart/
YOUR_TEMPLATE/jscript/
YOUR_TEMPLATE/popup_attributes_qty_prices/
YOUR_TEMPLATE/popup_coupon_help/
YOUR_TEMPLATE/popup_cvv_help/
YOUR_TEMPLATE/popup_image/
YOUR_TEMPLATE/popup_image_additional/
YOUR_TEMPLATE/popup_search_help/
YOUR_TEMPLATE/popup_shipping_estimator/
YOUR_TEMPLATE/sideboxes/
YOUR_TEMPLATE/templates/
```

As an example of this, if your template is called `bootstrap`, then to override `includes/templates/template_default/templates/tpl_product_info_display.php` you would create `includes/templates/bootstrap/templates/tpl_product_info_display.php`.

### Files in Other Places 
You can also place overrides in these folders: 
```
includes/auto_loaders/overrides/
includes/init_includes/overrides/
admin/includes/auto_loaders/overrides/
admin/includes/init_includes/overrides/
```

As an example of this, to override `admin/includes/init_includes/init_admin_auth.php`, you would create `admin/includes/init_includes/overrides/init_admin_auth.php`.


## What Can I NOT Override? 

At the moment, these folders of your cart do not support overrides:

- `admin` (except in the `auto_loaders` and `init_includes` folders, as noted above)
- `includes/modules/pages` (but you can add more files to a page's folder. See the [header_php.php Program Flow](/dev/code/program_flow/) developer documentation)
- The `shipping`, `payment` and `order total` folders under `includes/modules`

However, you may still modify their operation without changing core code by using [notifiers](/dev/code/notifiers/) and the other mechanisms described below.


## Other Mechanisms for Changing Cart Appearance  

Some behaviors are controlled by the [show flags](/user/customizing/show_flags/) in the admin.

Starting in 1.5.8, there are [site specific overrides](/user/customizing/site_specific_overrides/), which allow you to change some aspects of Zen Cart without touching core files. 

There are also other mechanisms to allow you modify the behavior of the system without touching core files.
These are more advanced topics, intended for developers. 

- [Notifiers/Observers](/dev/code/notifiers/)
- [Init System](/dev/code/init_system/)
- [Extra folders](/dev/code/extra_folders/)
- [Program Flow](/dev/code/program_flow/)

See also [plugin tips](/dev/plugins/tips/) for more suggestions. 

## Using your Overrides 

You've created some overrides and now you want to use your new template!

Just create the `template_info.php` file and activate your template. 
See [the template_info FAQ](/user/template/template_info/). 


## Next Steps 

- See [how to create a new template](/user/template/creating_template/).

- See [how to customize your new template](/user/template/basic_customizations/).

- Learn to use the [Developers Tool Kit](/user/admin/developers_toolkit/).
It will help you track down the files that you need to change to get the results you want. 


