---
title: Sorting an Admin menu 
description: How admin menus can be sorted 
category: code
weight: 10
---

By default, admin menus are sorted by the sort order of their entries.  However, since some menus are long, alphabetical sorting is more desirable. 

This was first done in Zen Cart 1.5.7, where the Tools menu is presented in alphabetical order. 

This can be controlled (and disabled) in `admin/includes/languages/english.php` in the category `MENU_CATEGORIES_TO_SORT_BY_NAME`.

To sort a Configuration menu entry (such as My Store) by name, modify `admin/configuration.php` to check the `$gID` parameter in the select at the start of the `tbody`, and order by `configuration_title` rather than `sort_order` for the desired menus. 
