---
title: Sorting an Admin menu 
description: How admin menus can be sorted 
category: code
weight: 10
---

## Top Level Menus (Configuration, Tools, etc.)

By default, the list under each of the main admin menu titles  (Configuration, Catalog, Modules etc...) are ordered according to each menu items `sort_order` in the database (which is set on initial installation). However, it is possible to alpha-sort these entries which may be more desirable as they often become extended with Plugins.

In Zen Cart 1.5.8 and above, this functionality is controlled in the admin main language file, eg.  `admin/includes/languages/lang.english.php` 

In Zen Cart 1.5.7, this functionality is controlled in the admin main language file, eg.  `admin/includes/languages/english.php` 

The constant which is set in these files is 

`MENU_CATEGORIES_TO_SORT_BY_NAME`

which sets a comma-separated list of the `menu_key` values to be sorted alphabetically.
(Note these values come from the `admin_menus` database table.)

The default value of the constant `MENU_CATEGORIES_TO_SORT_BY_NAME` is `reports,tools`, which means the Reports menu and the Tools menu are all sorted alphabetically.  To sort more menus alphabetically, add the desired menus to this list.

eg:
`'configuration,catalog,modules,customers,taxes,localization,reports,tools,gv,acccess,extras'`

## Sorting Sub-Menus under the Configuration Menu 

Under the Configuration menu (My Store, Minimum values etc,), the list in each submenu can also be alphasorted.

### Zen Cart 1.5.8
In release 1.5.8 and forward, the new constant `CONFIGURATION_MENU_ENTRIES_TO_SORT_BY_NAME` is used to determine which submenus are sorted by adding a comma-separated list of the configuration IDs (`gID`) of each submenu, 
e.g. '1,2,3,4' etc

The gID of each submenu can be ascertained by hovering the cursor over each submenu item and noting the number of the final parameter gID of the link,

eg. for Minimum Values:  https://MYWEBSITE/MY_ADMIN/index.php?cmd=configuration&**gID=2**

The default value of this constant it '1', which means that by default, only Configuration > My Store is alphabetically sorted; other configuration menus are sorted according to the `sort_order` value of each entry in a configuration group. 

### Zen Cart 1.5.7
In release 1.5.7, to sort a Configuration submenu listing (such as My Store) by name, `admin/configuration.php` must be modified manually to check for the `gID` of the desired menu and alter the SELECT query at the start of the tbody, to `ORDER BY configuration_title` instead of `ORDER BY sort_order` for that menu.

