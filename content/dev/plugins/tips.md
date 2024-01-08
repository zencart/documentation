---
title: Tips on creating a plugin 
description: Things to remember when creating a plugin for Zen Cart 
category: plugins
weight: 1
---

## Security

It is wise to ensure that ALL your PHP plugin files include a line near the top which checks whether `IS_ADMIN_FLAG` is defined. This way if you have a file that's accessed via unauthorized methods then it will just abort. For example:

`if (!defined('IS_ADMIN_FLAG')) die();`

Other variations for specific use in either admin or catalog might check whether it is set to boolean `true`/`false`.


## Optimizing the use of Overrides 

There are built-in override capabilities in Zen Cart to prevent needing to edit some core files which would otherwise need updating.

(As a reminder, the override basics are covered in the storefront help; 
you may read 
[the introduction](/user/first_steps/overrides/), 
[the details](/user/new_user_topics/overrides/), 
and then 
[the summary](/user/template/template_overrides/).)

Some of the commonly-overlooked override capabilities are listed here:

### database_tables.php & filenames.php
Combine your extra details for these two files into one file, and then add it to both the storefront and the admin:

`includes/extra_datafiles/my-contribution-name_datafiles.php`

`admin/includes/extra_datafiles/my-contribution-name_datafiles.php`

(these will auto-load)

### stylesheet.css
`includes/templates/YOURTEMPLATE/css/styles_my-contribution-name.css`

(This will auto-load)


## Do not auto delete your installer! 

Once upon a time someone thought it would be clever to delete the installation script after running it.  

A common pattern was to create a script in YOURADMIN/includes/init_includes (or perhaps YOURADMIN/includes/functions/extra_functions) which performed the installation and then deleted itself. 

Please note: THIS IS A TERRIBLE IDEA.  Don't do this.

The reason is simple.  Frequently people set up a test cart with a test database on their local machine in order to do an upgrade, and install all the files.  They will then install the same fileset on their live server at upgrade time.  If your installer auto-deletes, it won't be available for them when their live database is being used. 

A better practice is to check the database and see if the install has 
already been done. 

- Use `zen_page_key_exists`
- Check for specific configuration keys you would have added. 

<hr>

## Automatic New Version checks 

Use `plugin_version_check_for_updates` to call the Zen Cart plugin server so that users will know if you have a new release. See how this is done in an existing plugin such as [USPS](https://www.zen-cart.com/downloads.php?do=file&id=1292) or [Square Web Payments](https://www.zen-cart.com/downloads.php?do=file&id=2345). 

```
$new_version_details = plugin_version_check_for_updates(self::USPS_ZEN_CART_PLUGIN_ID, self::USPS_CURRENT_VERSION);
if ($new_version_details !== false) {
    $this->title .= '<span class="alert">' . ' - NOTE: A NEW VERSION OF THIS PLUGIN IS AVAILABLE. <a href="' . $new_version_details['link'] . '" target="_blank">[Details]</a>' . '</span>';
}
```

You can also provide a configuration flag for your plugin to disable these checks.  Some users won't want to do checks, either because they don't want the performance hit or they want to prevent their clients from worrying unnecessarily.  

If you want to do this, look at the example in [Colorbox for Zen Cart](https://www.zen-cart.com/downloads.php?do=file&id=1322). Search for `this_plugin_version_check_for_updates`. 


## Database change checks 

- Ensure your schema is correct.  See `tableCheckup` in `includes/modules/payment/paypal.php` for an example of how to do this.  You can also read more about the [sniffer object](/dev/code/database_querying/#sniffer-object) that does the required work. 

```
$fieldOkay1 = (method_exists($sniffer, 'field_type')) ? $sniffer->field_type(TABLE_PAYPAL, 'txn_id', 'varchar(20)', true) : -1;
 ... 

if ($fieldOkay1 !== true) {
  $db->Execute("ALTER TABLE " . TABLE_PAYPAL . " CHANGE payment_type payment_type varchar(40) NOT NULL default ''");
  ... 
```


- Ensure all required database entries are present in the configuration table.  Insert them if they are not.  See `keys` function in `includes/modules/payment/authorizenet.php`.

```
if (!defined('MODULE_PAYMENT_AUTHORIZENET_CURRENCY')) {
  $db->Execute("INSERT INTO " . TABLE_CONFIGURATION . " (configuration_title, configuration_key, configuration_value, configuration_description, configuration_group_id, sort_order, set_function, date_added) VALUES ('Currency Supported', 'MODULE_PAYMENT_AUTHORIZENET_CURRENCY', 'USD', 'Which currency is your Authnet Gateway Account configured to accept?<br>(Purchases in any other currency will be pre-converted to this currency before submission using the exchange rates in your store admin.)', '6', '0', 'zen_cfg_select_option(array(\'USD\', \'CAD\', \'GBP\', \'EUR\', \'AUD\', \'NZD\'), ', now())");
}
```

## Adding Configuration settings 

If your plugin requires new configuration data, see [Adding a configuration setting](/dev/plugins/adding_config/).

## Avoiding the Missing Menu problem 
If your plugin is an admin page, remember that some storeowners may want non-superusers to be able to run your utility.   Be sure you have created the relevant `admin_pages` table entries - see [Admin menu item is missing](/user/troubleshooting/admin_menu_item_missing/).

## Checking Zen Cart version

Your plugin may need to do something different depending on the Zen Cart version. Use the `PROJECT_VERSION_` settings in `includes/version.php` for this.  As an example, this checks for a Zen Cart version of 1.5.7 or higher: 

```
if ((PROJECT_VERSION_MAJOR . '.' . PROJECT_VERSION_MINOR) >= '1.5.7') {
```

For Zen Cart 1.5.7 and later, there is a helper function that you can use to simplify your code:

```php
if (zen_get_zcversion() >= '1.5.7') {}
```



## More Checks 

Since Zen Cart 1.5.8, all modules (shipping, payment and order_total) have supported an optional function called `get_configuration_errors`.  This allows a developer to verify the configuration settings and report on problems. 

## Other Resources 

- [Creating a menu item](/dev/code/creating_menu/)

- [Creating or altering tables](/dev/code/creating_tables/)

- [Building a form](/dev/code/forms/)


## Forum Resources 
If you run into trouble working on your plugin, you can always post your question on the [Contribution-Writing Subforum](https://www.zen-cart.com/forumdisplay.php?43-Contribution-Writing-Guidelines). 
