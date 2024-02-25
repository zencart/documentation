---
title: Template Settings and the tpl() function
description: Overriding global settings per-template
category: code
weight: 10
---

Starting with Zen Cart v2.0.0 there is a `tpl()` function which can be used to access site configuration settings that are customized to a specific template.

This means you can have the usual global settings configured in the Admin as usual, but allow for template-specific overrides which only take effect when a certain template is used.

One benefit of this for both storeowners and developers is the ability to try out a new template without destroying the existing configuration settings, so that your live site can function normally even while you're experimenting with new things.

It also allows template authors to distribute configuration settings with their template, without those settings messing with a store's already-configured settings.

> NOTE: This can be used in tandem with the `init_site_specific_non_db_settings.php` feature available since Zen Cart v1.5.8 - see [Site Specific Overrides](/user/customizing/site_specific_overrides/).


## Requirements

There are two requirements, using Zen Cart v2.0.0 or newer:
- the template must use `tpl()` to access settings instead of directly referring to the global CONSTANT
- the template's `/includes/templates/YOUR_TEMPLATE_NAME/template_settings.php` file must contain the override settings. (See the 2 kinds of overrides, explained below)



## Two Kinds of Settings Available

### 1. Overriding a CONSTANT such as an admin configuration setting

Many site configuration settings used by templates (and modules that supply data to templates) are controlled via the Admin configuration pages.

Here's an example of how to override the setting by making an adjustment to your template file and defining the override separately for each template which desires to use something other than the Admin configuration setting.

#### Example: Banner Group #2

Zen Cart's banner feature can be used to show in-site ads or offsite ads or other messages to customers. Some templates use the feature to control a gallery/slider-effect of images.

Banners are rendered in various positions of the template, and it's possible that one template wants the feature turned off completely, but another template leverages it specifically. This is a good time to use template-specific settings.

1. **Determine the CONSTANT** that is used in the Admin for accessing the configured value. The Developers Toolkit can be useful here. If looking in the database at the `configuration` table, it's the `configuration_key` that we're looking for, because a CONSTANT is declared for the `configuration_key`, with its value set to what's stored in `configuration_value`.

  In the case of our example, we're looking at the controls for `SHOW_BANNERS_GROUP_SET2`.

2. **Replace the constant with tpl() in the template.** 

  Look in your template files for wherever that `SHOW_BANNERS_GROUP_SET2` constant is used, and replace the constant with a function call to `tpl()` whose first parameter is that constant.

  eg:
```php
  if (SHOW_BANNERS_GROUP_SET2 != '' && $banner = zen_banner_exists('dynamic', SHOW_BANNERS_GROUP_SET2)) {
```
becomes the following, where two replacements are made:
```
  if (tpl('SHOW_BANNERS_GROUP_SET2') != '' && $banner = zen_banner_exists('dynamic', tpl('SHOW_BANNERS_GROUP_SET2'))) {
```

  To test, things should work as they did before, without any change yet because we haven't configured an override setting yet. We'll do that next:

3. Set the new value into the `$tpl_settings` array in `template_settings.php`:

  In your template's `template_settings.php` file, find the list of array entries for `$tpl_settings`, and add one for the setting you're overriding.
  
  eg: `$tpl_settings['SHOW_BANNERS_GROUP_SET2'] = 'current_promotions';`

  You can now refresh the template page in your browser, and the new banner group will be applied. (Of course, you will have to have already defined a banner group by the name you're using here. If the banner group exists and banners are assigned to it, they will be displayed.)


### 2. Defining a public variable that is used someplace in a template or module file.

Sometimes templates or modules are coded to be alert to the pre-existence of a variable that could be overridden by setting it earlier in the PHP code execution process.

Defining such variables is sometimes referred to as a "soft" setting/override.

#### Example:
The `product_listing.php` module has the ability to specify some CSS classes that should be applied to the grid used when in "fluid" mode (where Product Listing Columns Per Row is set to '0').

If your template doesn't need to customize anything other than the CSS style class names for the product-listing to display as desired, you could define those classes in `template_settings.php` instead of creating an override module file and directory for `product_listing.php`.

The `responsive_classic` template sets the following variables in its `template_settings.php` file to define those CSS classes:

```php
$grid_product_cards_classes = 'row row-clmns-3';
$grid_product_classes_matrix = [
    '480' => 'row row-clms-1 row-clms-sm-2 row-clms-md-3 row-clms-lg-4 row-clms-xl-6',
];
```



## Potential Conflicts

Be aware that if you are setting any of these public/"soft" variables using the `site-specific-settings`, there might be a clash. See the Technical Information For Developers section below for troubleshooting clashes.

## Using `template_settings` in tandem with `init_site_specific_non_db_settings.php`

It is recommended to put template-specific settings into the `template_settings.php` file.


You may leave your preferred site-wide defaults as variables in `init_site_specific_non_db_settings.php`, but they will be overridden by `template_settings.php` when it is loaded.

This can work in your favor.



## Technical Information for Developers

### Load Order
Zen Cart loads certain features/settings in a prescribed order. If you have a setting defined earlier in the process, it will be overridden if something else defines the same thing later on.

Also, due to the way PHP works, any CONSTANTs you've defined earlier in the process will NOT be overridden/definable later in the process, since they can only be defined once.

Related init-system load-order information:
- `extra_datafiles` including `site_specific_overrides` before breakpoint 0
- db CONSTANTs (admin-defined config settings) at breakpoint 40
- non-db CONSTANTs and variables in `init_non_db_settings` and `init_site_specific_non_db_settings.php` at breakpoint 45
- `functions` and `extra_functions` files at breakpoint 60
- `template_settings.php` at breakpoint 110
- followed by language-defines and `extra_definitions` for the current language

### About the `tpl()` helper function

#### Lookup Order

The `tpl()` function looks for a value to return using this order:

1. The global $tpl_settings array for a key matching the $setting requested
2. A defined CONSTANT matching the $setting requested
3. Optionally, a global $var of the name of the $setting requested
4. If nothing is found, the supplied default will be returned
5. Else `null` is returned


#### Function Parameters
There are some advanced features available to the `tpl()` helper function.

Here is the function signature:
`function tpl(string $setting, string $cast_to = null, $default = null, bool $check_globals = false): mixed`

- `$setting` is the lookup key;
- `$cast_to` lets you specify a (basic) PHP type to cast the returned value to. This saves you having to cast it separately after getting the response back;
- `$default` is the value that is returned if the `$setting` is not found in `$tpl_settings` array and not defined as a CONSTANT;
- `$check_globals` allows you to tell it to also check for a global variable named the same as the $setting (case will be checked for exact-match to `$setting`, and also the all-lower-case form, eg `strtolower($setting)`).


Advanced: You "could" query *any* constant and cast its value to a certain type.

Or you "could" query *any* constant, and if not found, have it return your supplied default value.

