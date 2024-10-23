---
title: What to translate
description: Finding strings to translate and format them to ZC constants and languages files before translation
weight: 100 
layout: docs
---

With Zen Cart v2.1.0 language can be switched smoothly, even admin menus, modules and plugins.

Unfortunately for language pack makers, finding strings to translate might be a challenge. Here is a list of places where you will find these strings. Then few tools are provided to convert to Zen Cart language files constants, ready for translation.

<hr>

### Language files:

Strings to translate are already in files where they will be used, no extra formatting is necessary.

**Zen Cart core language files:**

These are the eaisiest to find and prepare for translation. You only have to copy all the 'english' folders and rename them to your new language, then you are ready to translate content.

- admin/includes/languages/english/
- includes/languages/english/
- zc_install/includes/languages/english/
- zc_plugins/DisplayLogs/vx.x.x/admin/includes/languages/english/
- zc_plugins/POSM/vx.x.x/admin/includes/languages/english/
- zc_plugins/POSM/vx.x.x/catalog/includes/languages/english/
- zc_plugins/POSM/vx.x.x/installer/languages/english/
- zc_plugins/SystemInspection/x.x.x/admin/includes/languages/english/
- zc_plugins/SystemInspection/x.x.x/installer/languages/english/


Note: 'x' represent numbers depending on plugin version.

**Images (buttons):**

Those are actually images files used for buttons. You will need an image editor to create new buttons. They can be replaced by css buttons in admin setting. In this case you don't need to recreate new buttons. If you do, don't forget to rename your new buttos' folder to your language.

- includes/templates/template_default/buttons/english

**Hard coded strings:**

This text is only visible once before installing ZC and you try to load the index of your site. At this time there is no language system loaded and it is why these strings are hard coded in files. If instead of loading index page, you load ZC installer directly (../zc_installer), you won't even see this. Choice is yours to translate it or not.

- includes/templates/template_default/templates/tpl_zc_install_suggested_default.php
- includes/templates/template_default/templates/tpl_zc_phpupgrade_default.php


### Database fields:

**Database configuration menus:**

These are all the admin menus and submenus. You can find them in files before intallation, but on an installed English cart, they are in database, at least for parts that have been installed. Most of the standards admin configuration strings go in the file `lang.configuration.php` but for modules and plugins, it is more complicated and it will be expained in a 'Formatting' chapter below. In any case, reformating these strings into PHP constants format will be necessary.

##### IN FILES:

***Standard admin configuration settings***

These are in this file `zc_install/sql/install/mysql_zencart.sql`.
On all lines starting by:

`'INSERT INTO configuration'` or `'INSERT IGNORE INTO configuration'`, look for values of fields `'configuration_title'` and `'configuration_description'`.

`'INSERT INTO configuration_group'`, look for values of fields `'configuration_title'` (second one) and `'configuration_description'` (third one).

`'INSERT INTO product_types'`, look for values of second field `'type_name'`.

`'INSERT INTO product_type_layout'`, look for values of fields `'configuration_title'` and `'configuration_description'`.


***For modules shipping, payment and order total:***

`includes/modules/(shipping, payment or order_total)/MODULE_NAME.php`, look for `'function install()'` which contains SQL queries with `'configuration_title'` and `'configuration_description'`.


***Encapsulated plugins names and description:***

`zc_plugins/PLUGIN_NAME/PLUGIN_VERSION/manifest.php`, look for `'pluginName'` and `'pluginDescription'` definitions.


***Encapsulated plugins admin menus:***

`zc_plugins/PLUGIN_NAME/PLUGIN_VERSION/Installer/ScriptedInstaller.php`, look for SQL queries (structure depending on plugins) on configuration and configuration_group tables. You should find key title and descrition.

***Non-encapsulated plugins admin menus:***

If the plugin auto install when opening admin page, then settings definitions to translate should be in a file like this:
`admin/includes/init_includes/init_PLUGIN_NAME.php`, look for SQL queries on configuration and configuration_group tables.
Another possibilty is to look in admin menu for this plugin related menus, but chance to miss some of them is high.
If the plugin does not install automatically, chances are there is an SQL file to import. Here too, strings we are looking for are in those queries to configuration and configuration_group tables.


##### IN DATABASE:

Modules or plugins not installed won't have their English strings registered in database! Everything installed will be in one of these tables:

- Table `'configuration'`, fields `'configuration_title'` and `'configuration_description'`.

- Table `'configuration_group'`, fields `'configuration_title'` and `'configuration_description'` (not really used).

- Table `'product_types'`, field `'type_name'`.

- Table `'product_type_layout'`, fields `'configuration_title'` and `'configuration_description'`.

- Table `'plugin_control'`,  fields `'name'` and `'description'`.


### Database fields to be translated through admin interface:

These are dependant on data imput by users like adding products and other customization and by definition are subject to change. Admin interface will allow you to add or update these strings in all installed languages.


Table **`'categories_description'`**, fields `'categories_name'` and `'categories_description'`.
Menu : **Catalog::Categories/Products -> Click on 'Edit' icon for a category**.


Table **`'meta_tags_categories_description'`**, fields `'meta_tags_title'`, `'meta_tags_keywords'` and `'meta_tags_description'`.
Menu : **Catalog::Categories/Products -> Click on 'Edit Meta Tags' icon for a category**.


Table **`'coupons_description'`**, fields `'coupon_name'` and `'coupon_description'`.
Menu : **Discounts::Coupon Admin -> Select a coupon and click on 'Edit' button**.


Table **`'ezpages_content'`**, fields `'pages_title'` and `'pages_html_text'`.
Menu : **Tools::EZ-Pages -> Select a page and click on 'Edit' button**.


Table **`'products_description'`**, fields `'products_name'` and `'products_description'`.
Menu : **Catalog::Categories/Products -> Click on category until product listing displays -> Click on 'Edit Product' icon for a product**.

Table **`'meta_tags_products_description'`**, fields `'meta_tags_title'`, `'meta_tags_keywords'` and `'meta_tags_description'`.
Menu : **Catalog::Categories/Products -> Click on category until product listing displays -> Click on 'Edit Meta Tags' icon for a product**.


Table **`'products_options'`**, fields `'products_options_name'` and `'products_options_comment'`.
Menu : **Catalog::Option Name Manager -> Click on 'Edit' button for an option**.


Table **`'orders_status'`**, field `'orders_status_name'`.
Menu : **Localization::Orders Status -> Select a status and click on 'Edit' button**.


If POSM has been installed:
Table **`'products_options_stock_names'`** field `'pos_name'`.
Menu : **Catalog::Manage Options' Stock -> Click on 'Define Labels' button -> Select a label and click on 'Edit' button**.

<hr>

## Formating database language strings for translation and use:

As we have seen above, language strings in database are not easy to retrieve and even translated they need to be formated to fit in language files. Here is a possible worflow that will makes things easier.

First step is to copy all lines from file `zc_install/sql/install/mysql_zencart.sql` that contain these strings, as decribed in chapter abobe, to a new text or php file.

Then using a text editor with regular expression capabilities, second step is to convert these lines to PHP constants definition format like those used in language files.

Third step is to put these constants definitions in the right language file where they are ready to be translated and used.


### Converting SQL language strings to PHP constants strings:


#### Standard admin menus and submenus:

As written above there are four SQL tables of interest, `'configuration'`, `'configuration_group'`, `'product_types'` and `'product_type_layout'`. It is eaier to take care of them one by one. After copying SQL INSERT queries from **`zc_install/sql/install/mysql_zencart.sql`** file, the following regular expressions will be very handy:

***Table configuration:***
Find:
`^INSERT (IGNORE ){0,1}INTO configuration \(configuration_title, configuration_key, configuration_value, configuration_description, configuration_group_id, sort_order, date_added\) VALUES \('(.*)', '([A-Z_0-9]*)', '.*', '(.*)', '?\d+'?, '?\d+'?, now\(\)\);$`

Replace with:
`\s{4}'CFGTITLE_$3' => '$2',\r\s{4}'CFGDESC_$3' => '$4',`

Result goes in file **`admin/includes/languages/YOUR_NEW_LANGUAGE/lang.configuration.php`**.


***Table configuration_group:***
Find:
`^INSERT INTO configuration_group VALUES \([0-9]*, '((\S*)|((\S*)\s(\S*))|((\S*)\s(\S*)\s(\S*)))', '(.*)', '?\d+'?, '?\d+'?\);$`

Replace with:
`\s{4}'CFG_GRP_TITLE_\U$2${3:+$4_$5:}${6:+$7_$8_$9:}\E' => '$10',`

Result goes in file **`admin/includes/languages/YOUR_NEW_LANGUAGE/lang.configuration.php`**.


***Table product_types:***
Find:
`^INSERT INTO product_types VALUES \([0-9]*, '(((\S*)\s-\s(\S*))|((\S*)\s-\s(\S*)\s(\S*)))', '.*\);$`

Replace with:
`\s{4}'PRODUCT_TYPE_NAME_FOR_HANDLER_\U${2:+$3_$4:}${5:+$6_$7_$8:}\E' => '$1',`

Result goes in file **`admin/includes/languages/YOUR_NEW_LANGUAGE/lang.product_types.php`**.


***Table product_type_layout:***
Find:
`^INSERT INTO product_type_layout \(.*\) VALUES \('(.*)', '([A-Z_0-9]*)', '\d+', '(.*)', '?\d+'?, '?\d+'?,.*, now\(\)\);$`

Replace with:
`\s{4}'PRODUCT_TYPE_LAYOUT_TITLE_FOR_$2' => '$1',\r\s{4}'PRODUCT_TYPE_LAYOUT_DESC_FOR_$2' => '$3',`

Result goes in file **`admin/includes/languages/YOUR_NEW_LANGUAGE/lang.product_types.php`**.


#### Modules admin menus and submenus:

To get all language strings you need to go through each modules files in **`includes/modules/`** respectively `shipping`, `payment` and `order_total` folders. After converting these put the results in modules respective language file `lang.MODULE_NAME.php`. This will make updates and maintenance easier.

Find:
`^\s*\$db->Execute.* \('(.*)', '([A-Z_0-9]*)'?, '.*', '(.*)', '?\d+'?, '?\d+'?,? ?'?.*'?, now\(\)\)"\);$`

Replace with:
`\s{4}'CFGTITLE_$2' => '$1',\r\s{4}'CFGDESC_$2' => '$3',`

For **shipping modules**, result goes in file **`includes/languages/YOUR_NEW_LANGUAGE/modules/shipping/lang.MODULE_NAME.php`**.

For **payment modules**, result goes in file **`includes/languages/YOUR_NEW_LANGUAGE/modules/payment/lang.MODULE_NAME.php`**.

For **order total modules**, result goes in file **`includes/languages/YOUR_NEW_LANGUAGE/modules/order_total/lang.MODULE_NAME.php`**.



#### Encapsulated plugins admin menus and submenus:

There are actually 3 encapsulated plugins, `Display logs`, `Products' Options' Stock Manager` and `System Inspection` included by default in Zen Cart.

Plugin *name* and *description* language strings are in manifest files (**`zc_plugins/PLUGIN_NAME/PLUGIN_VERSION/manifest.php`**) and *menus* and *submenus*, if they exist, are in installer files (**`zc_plugins/PLUGIN_NAME/PLUGIN_VERSION/Installer/ScriptedInstaller.php`**).
Unfortunately, SQL queries in installer files are very variable and conversion can not be done with only one regular expression.

**Create a new file `zc_plugins/PLUGIN_NAME/PLUGIN_VERSION/admin/languages/NEW_LANGUAGE/extra_definitions/lang.PLUGIN_NAME.php`** with this content, replacing key, title and description by each plugin actual data:

```
<?php
$define = [
    'ADMIN_PLUGIN_MANAGER_NAME_FOR_module_key' => 'MODULE NAME',
    'ADMIN_PLUGIN_MANAGER_DESCRIPTION_FOR_module_key' => 'MODULE DESCRIPTION',
];

return $define;
```


For *admin menus* and *submenus*, convert using appropriate regular expression and add results to file created above.

***Regular expression for Display Logs:***
Copy lines from **`$this->addConfigurationKey(`** to **`'configuration_description' =>`** and regroup them in one line. Do this for each query, then apply regular expression.

Find:
`^.*addConfigurationKey\('([A-Z_0-9]+).*configuration_title' => '(.*)',\s+'configuration_value' =>\s+'.*',\s*'configuration_description' => '(.*)',$`

Replace with:
`\s{4}'CFGTITLE_$1' => '$2',\r\s{4}'CFGDESC_$1' => '$3',`

Add result to file created above.

***Regular expression for POSM:***

Copy all lines between `VALUES` and `$this->executeInstallerSql($sql);`, then apply regular expression.

Find:
`^\s*\('(.*)', '([A-Z_0-9]*)', '.*', '(.*)', \$.*$`

Replace with:
`\s{4}'CFGTITLE_$2' => '$1',\r\s{4}'CFGDESC_$2' => '$3',`

Add result to file created above.

*Note*: `System Inspection` plugin do not have any extra admin menu to translate.

#### Non-encapsulated plugins admin menus and submenus:

In this case, as seen above, data to translate would be in a `admin/includes/init_includes/init_PLUGIN_NAME.php` file or a separate SQL file.
Like for encapsulated plugins a new language file needs to be created but in `admin/includes/languages/NEW_LANGUAGE/extra_definitions/lang.PLUGIN_NAME.php`. Actual filename is not important, it is yours to choose. Content at first should be like this:
```
<?php
$define = [
    'CFGTITLE_plugin_key' => 'PLUGIN KEY TITLE',
    'CFGDESC_plugin_key' => 'PLUGIN KEY DESCRIPTION',
    .
    .
    .
];

return $define;
```
Here is an example for the French version of Image Handler plugin:
```
<?php

$define = [
    'CFGTITLE_IH_RESIZE' => 'IH redimensionne les images',
    'CFGDESC_IH_RESIZE' => 'Sélectionnez soit -no- qui est l\'ancien comportement de Zen-Cart, soit -yes- pour activer le redimensionnement automatique et la mise en cache des images. --Remarque : Si vous sélectionnez -no-, tous les paramètres d\'image spécifiques au gestionnaire d\'images ne seront pas disponibles, notamment : sélection du type de fichier image, couleurs d\'arrière-plan, compression, survol de l\'image et filigrane - Si vous souhaitez utiliser ImageMagick, vous devez spécifier l\'emplacement de l\'exécutable <strong>de conversion</strong> dans <em>includes/extra_configures/bmz_image_handler_conf.php</em>.',
    'CFGTITLE_IH_VERSION' => 'Version d\'IH',
    'CFGDESC_IH_VERSION' => 'Affiche la version actuellement installée d\'<em>Image Handler</em>.',
    'CFGTITLE_IH_CACHE_NAMING' => 'Convention de dénomination des fichiers de cache d\'IH',
    'CFGDESC_IH_CACHE_NAMING' => '<br>Choisissez la méthode utilisée par <em>Image Handler</em> pour nommer les images redimensionnées dans le répertoire <code>bmz_cache</code>.<br><br><em>Hashed</em> : Utilise un hache &quot;MD5&quot; pour produire les noms de fichiers. Cela peut être « difficile » pour identifier visuellement le fichier original en utilisant cette méthode.<br><br><em>Readable</em> : C\'est un bon choix pour les nouvelles installations de <em>IH</em> ou pour les installations mises à niveau qui n\'ont pas de liens d\'images codés en dur.<br><br><em>Mirrored</em> : Similaire à <em>Readable</em>, mais la structure des répertoires dans <code>bmz_cache</code> reflète la structure des sous-répertoires des images d\'origine.',
];

return $define;
```

It is impossible to provide a regular expression here as it is too much dependent on plugin. But some of those provided above might work or just need a little tweak.