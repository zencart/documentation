---
title: Template Overrides System 
description: Zen Cart Template Overrides System 
category: template 
weight: 10
---

Before you read this, please review 
[basic terms](/user/first_steps/basic_terms/),
[template default and default files](/user/first_steps/overrides/) and 
[overrides for new users](/user/new_user_topics/overrides). 

## Introduction 

Overrides were created to simplify upgrading and templating. 

## What Can I Override? 
Any file which exists in a folder which has a `classic` subfolder 
can be overridden. 

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
YOUR_TEMPLATE/template_info.php/
YOUR_TEMPLATE/templates/
```

You can also place overrides in these folders: 
```
./includes/auto_loaders/overrides/
./includes/init_includes/overrides/
./admin/includes/auto_loaders/overrides/
./admin/includes/init_includes/overrides/
```

## Other Mechanisms 
There are also other mechanisms to allow you modify the 
behavior of the system without touching core files.
These are more advanced topics, intended for developers. 

- [Notifiers/Observers](/dev/code/notifiers/)
- [Init System](/dev/code/init_system/)
- [Extra folders](/dev/code/extra_folders/) 

See also [plugin tips](/dev/plugins/tips) for more suggestions. 

## Using your Overrides 

Once you have created one or more of these override folders, you can 
start using them by doing these two things: 

a. Create `includes/templates/YOURTEMPLATE/template_info.php`

In order for the system to "see" your template, the `template_info.php`
file must exist inside the `includes/templates/YOURTEMPLATE` folder. 

Create it as follows: 
```
<?php 
$template_name = 'Your Template Name'
``` 

b. Login to your Admin panel and go to [Tools > Template Selection](/user/admin_pages/tools/template_selection/).  You should see your new custom template(s) in the dropdown list. Select your template.


## Next Steps 

- See [how to create a new template](/user/template/creating_template).

- See [how to customize your new template](/user/template/customizing_template).

- Learn to use the [Developers Tool Kit](/user/admin/developers_toolkit).
It will help you track down the files that you need to change to get the results you want. 


