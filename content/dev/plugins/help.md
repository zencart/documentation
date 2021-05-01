---
title: Technical - Building help for your admin plugin 
description: Creating easy-to-access help for your Zen Cart admin-side modification
category: plugins
weight: 10
---

{{< technical >}}

## Help for New Admin Pages 

If your plugin creates a new page, the ability to provide help has been built-in since Zen Cart 1.5.8.  If you are not yet using this version or higher, you can merge [this PR](https://github.com/zencart/zencart/pull/4243/commits/ea92e4a950ba0c373ec081a3472d16f5030a70c1) into your cart. 

Use the [observer autoloading](https://docs.zen-cart.com/dev/code/notifiers/#auto-loaded-observers) feature of Zen Cart admin observers (available since Zen Cart 1.5.7), and create a new file called `admin/includes/classes/observers/auto.MyPluginHelp.php`.  (Be sure to follow the naming conventions for observer autoloading!)

```
<?php
class zcObserverMyPluginHelp extends base {
  function __construct() {
    $this->attach($this, array('NOTIFIER_PLUGIN_HELP_PAGE_URL_LOOKUP'));
  }

  function update(&$class, $eventID, $page, &$help_page) {
     if ($eventID == 'NOTIFIER_PLUGIN_HELP_PAGE_URL_LOOKUP') {
        if ($page == FILENAME_MYPLUGIN_NAME) {
           $help_page = "link-to-your-help-page"; 
        }
     }
  }
}
```

If you are not running Zen Cart 1.5.7 or higher, you will need to pull in [this PR](https://github.com/zencart/zencart/commit/bc195baf258c11b73f29de41020e1c0505e4d462) to your cart to get admin observers to autoload. 

## Help for Modules (Shipping, Payment or Order Totals) 

Module help is another feature which has been built-in since Zen Cart 1.5.8.  If you are not yet using this version or higher, you can merge [this PR](https://github.com/zencart/zencart/commit/77d4434ed5469c2f65e79a890ac6a4cb4fe85ac4) into your cart. 

The help function returns an array. If the array key `link` is set, then pressing the Help button will open a new tab for that link.  If the key `body` is set, then the value data for `body` will be displayed in a modal dialog.

## Examples of PHP Help Files 

Quite often plain text help (i.e. a `.html` file) is perfectly adequate, but if you need to make reference to the values of settings, pull in files, or do other dynamic operations, you'll want to use a `.php` help file.

### Setup 
To have access to database settings, functions, and everything else, you need to pull in the configure file.  This is a two step process since you're not at the top level of either admin or the storefront.  First, `chdir` to the admin (or catalog) folder, then pull it in.

```
<?php 
chdir("..");
require 'includes/application_top.php';
?>
```

You still have to account for being in a subfolder when building links - see examples below. 

### Displaying and Linking to Config values in Core menus 

Suppose you created a database entry with configuration key SPECIAL_FEE in the Admin > Configuration > My Store section.  Here's how you could access it and reference it: 

```
<?php
echo 'Current Special Fee is $' . SPECIAL_FEE . '.<br><br>';
echo 'To change this value, go to <a href="../configuration.php?gID=1" target="_blank">Admin > Configuration > My Store</a> <br>';
?>
```

### Displaying and Linking to Config values in Plugin menus 

If you don't know what the group id is, you have to query it. 
Rather than querying the group title (a text string that could change), query the configuration group of a specific key in that group. 

```
<?php 
$group = $db->Execute("SELECT * FROM " . TABLE_CONFIGURATION . " WHERE configuration_key = 'PO_SEND_PACKING_LISTS'");
$gID = $group->fields['configuration_group_id'];
echo 'Settings for this plugin are configured in <a href="'  . HTTPS_CATALOG_SERVER . DIR_WS_ADMIN . '../configuration.php?gID=' . $gID . '" target="_blank">Admin > Configuration > Dropship Purchase Orders</a> <br>';
?>
```

### Collaborating on Help 

If you need to allow multiple people to update the help simultaneously, consider linking out to a collaboration tool such as Google Docs. 

### Pulling in a function 

If you have created a function with a bunch of hardcoded cases that the storeowner needs to refer to (perhaps to tell you when to add a new one), you can use reflection to show the code. 

```
$func = new ReflectionFunction('name-of-function');
$filename = $func->getFileName();
$start_line = $func->getStartLine() - 1;
$end_line = $func->getEndLine();
$length = $end_line - $start_line;

$source = file($filename);
$body = implode("", array_slice($source, $start_line, $length));
echo '<pre>';
print_r($body);
echo '</pre>';
```

### Putting help files on a server 

If you are deploying help files to a newly created folder, be sure to follow the guidelines in [Direct Access to Files](/user/customizing/add_pages/#direct-access-to-files). 

