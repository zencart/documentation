---
title: Sorting an Admin menu 
description: How admin menus can be sorted 
category: code
weight: 10
---

By default, the list under each of the main admin menu titles  (Cofiguration, Catalog, Modules etc...) are ordered according to each items sort_order as defined in the database, which is set on initial installation. However, it is possible to alphasort these entries. 

This functionality is controlled in the admin main language file, eg.  `admin/includes/languages/english.php` 

by the constant

`MENU_CATEGORIES_TO_SORT_BY_NAME`

by adding a comma-separated list of the menu_key values (as defined in the admin_menus database table)

eg:
`'configuration,catalog,modules,customers,taxes,localization,reports,tools,gv,acccess,extras'`

Under the Configuration menu (My Store, Minimum values etc,), the list in each submenu can also be alphasorted by the constant

 `CONFIGURATION_MENU_ENTRIES_TO_SORT_BY_NAME`

by adding a comma-separated list of the configuration IDs (gID) of each submenu, 
e.g. '1,2,3,4' etc

The gID of each submenu can be ascertained by hovering the cursor over each submenu item and noting the number of the final parameter gID of the link,

eg. for Minimum Values:  https://MYWEBSITE/MY_ADMIN/index.php?cmd=configuration&**gID=2**
