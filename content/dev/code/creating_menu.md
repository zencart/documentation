---
title: Creating a new menu item 
description: Creating a new menu item in Zen Cart 
category: code
weight: 10
---

Every time I'm adding a new item to my v1.5.x admin, I search the forums and can never find the post (I know it's there) that identifies how to  get your new tool added to the admin menu ... so I'm noting the process  here.  

 Let's say that you have a new tool named `new_tool.php` that you want to plug into the ***Tools*** menu.

 Most of the files that you distribute in the `new_tool.zip` file are identical with previous Zen Cart versions:

1. `/YOUR_ADMIN/new_tool.php`.  Contains the code that implements your new tool.

2. `/YOUR_ADMIN/includes/extra_datafiles/new_tool_filenames.php`.  Contains the filename definition for your new tool, e.g. `define('FILENAME_NEW_TOOL', 'new_tool');`.

3. `/YOUR_ADMIN/includes/languages/english/extra_definitions/new_tool_name.php`.  Contains the menu entry text definition for your new tool, e.g. `define('BOX_TOOLS_NEW_TOOL', 'New Tool');`.

4. `/YOUR_ADMIN/includes/languages/english/new_tool.php`.  Contains the language-specific defines for your new tool; the filename of the language file *must be the same* as  the filename of the tool itself.

The file that you distribute to actually add `new_tool.php` to the ***Tools***  menu is different for v1.5.0 and later. In previous versions of Zen  Cart, you would have distributed a file named `/YOUR_ADMIN/includes/boxes/extra_boxes/newtool_tools_dhtml.php` containing

```php
$za_contents[] = array(
    'text' => BOX_TOOLS_NEW_TOOL, 
    'link' => zen_href_link(FILENAME_NEW_TOOL, '', 'SSL')
);
```

For Zen Cart v1.5.0 and later, you can include a single file, `/YOUR_ADMIN/includes/functions/extra_functions/init_new_tool.php`, if you don't want to issue a message indicating that the tool has been installed.  Those `extra_functions` files are run _prior to_ any language-file loading.  If you want to display a message indicating that your tool has been installed, you'll need two  (`/YOUR_ADMIN/includes/auto_loaders/config.new_tool.php` and `/YOUR_ADMIN/includes/init_includes/init_new_tool.php`) files to provide this action. 

For the second case, the `config.new_tool.php` file will contain something similar to:

```php
$autoLoadConfig[200][] = array(
    'autoType' => 'init_script',
    'loadFile' => 'init_new_tool.php'
);
```

In *either* case, the `init_new_tool.php` will contain something like:

```php
if (!defined('IS_ADMIN_FLAG')) {
    die('Illegal Access');
} 

//----
// If the installation supports admin-page registration (i.e. v1.5.0 and later), then
// register the New Tools tool into the admin menu structure.
//
// NOTES:  
// 1) Once this file has run once and you see the Tools->New Tool link in the admin
// menu structure, it is safe to delete this file (unless you have other functions that
// are initialized in the file).
// 2) If you have multiple items to add to the admin-level menus, then you should 
// register each of the pages here, just make sure that the "page key" is unique or 
// a debug-log will be generated!
//
if (function_exists('zen_register_admin_page')) {
    if (!zen_page_key_exists('toolsNewTool')) {
        zen_register_admin_page(
            'toolsNewTool', 
            'BOX_TOOLS_NEW_TOOL', 
            'FILENAME_NEW_TOOL',
            '' , 
            'tools', 
            'Y'
        );
    }    
}
```

- The value *toolsNewTool* is a (hopefully) unique value that identifies your new tool.
- The values `BOX_TOOLS_NEW_TOOL` and `FILENAME_NEW_TOOL` are defined within the other files within your toolset.
- The fourth parameter ('') has any parameters that your tool might require.  Rarely used, except when you're adding a configuration-page element.
- The fifth parameter (`'tools'` in the example) identifies which of the  high-level menu items your tool "attaches" to, one of: configuration,  catalog, modules, customers, taxes, localization, reports, tools, gv,  access, or extras.
- The sixth parameter ('Y') identifies whether ('Y') or not ('N') to display the page on the admin menu.
- The seventh (optional) parameter is the sort order for the page, i.e. where it  lives on the drop-down menu in relation to the sort order of others.  Leave this entry empty and the function will place `new_tool` at the bottom of the selected menu dropdown.

To remove your menu item, in the case a store-owner chooses to  un-install your plugin, simply include a file in your distribution  zip-file named  `/uninstall_new_page.sql` that contains

```sql
DELETE FROM admin_pages WHERE page_key = 'toolsNewTool';
```

**Notes:**

- Instead of distributing the `init_new_tool.php` file, you could include instructions to install using the ***Admin Access  Management->Admin Page Registration*** tool.
  1. Set *Page Key* to `toolsNewTool`
  2. Set *Page Name* to `BOX_TOOLS_NEW_TOOL`
  3. Set *Page File Name* to `FILENAME_NEW_TOOL`
  4. Leave *Page Parameters* blank
  5. Select "Tools" from the *Menu* dropdown
  6. Check the *Show on Menu* box
  7. (optional) Set the *Sort Order* value to position your new tool on the displayed menu dropdown.
- If you don't see your newly added item, it's likely somewhere in the middle of the menu's dropdown list.
- Use 999 (or any other large number) for the sort order value if you want to ensure that your item is at the bottom of the menu's list.
- To reposition an item within one of the admin menus, use your cPanel's phpMyAdmin tool and  browse the `admin_pages` table to find the added menu item and adjust its  sort_order value as desired.


Thanks to Mega Moonshine for suggesting improvements made to this article on 2013-11-30!