---
title: Sorting an Admin menu 
description: How admin menus can be sorted 
category: code
weight: 10
---

By default, the list under each of the main admin menu titles  (Configuration, Catalog, Modules etc...) are ordered according to each menu items `sort_order` in the database (which is set on initial installation). However, it is possible to alpha-sort these entries which may be more desirable as they often become extended with Plugins.

Since Zen Cart 1.5.7, this functionality has been controlled in the admin main language file, eg.  `admin/includes/languages/english.php` 

by the constant

`MENU_CATEGORIES_TO_SORT_BY_NAME`

by adding a comma-separated list of the menu_key values (as defined in the admin_menus database table)

eg:
`'configuration,catalog,modules,customers,taxes,localization,reports,tools,gv,acccess,extras'`

Additionally under the Configuration menu (My Store, Minimum values etc,), the list in each submenu can also be alphasorted.

### Zen Cart 1.5.7
In release 1.5.7, to sort a Configuration submenu listing (such as My Store) by name, `admin/configuration.php` must be modified manually to check for the `gID` of the desired menu and alter the SELECT query at the start of the tbody, to `ORDER BY configuration_title` instead of `ORDER BY sort_order` for that menu.

### Zen Cart 1.5.8
In release 1.5.8 and forward, the new constant `CONFIGURATION_MENU_ENTRIES_TO_SORT_BY_NAME` is used to determine which submenus are sorted by adding a comma-separated list of the configuration IDs (`gID`) of each submenu, 
e.g. '1,2,3,4' etc

The gID of each submenu can be ascertained by hovering the cursor over each submenu item and noting the number of the final parameter gID of the link,

eg. for Minimum Values:  https://MYWEBSITE/MY_ADMIN/index.php?cmd=configuration&**gID=2**
