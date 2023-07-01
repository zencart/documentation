---
title: Language Files - Developer Information on Array based Language files
description: Structure of Language Packs for Zen Cart 1.5.8 and above 
weight: 10 
layout: docs
---

In Zen Cart 1.5.8, the language file structure was modified so that the PHP `define` statement is no longer used directly to set a language constant.  The reason for this is that newer versions of PHP will emit warning messages when a constant is redefined (in an override vs core file), so the old approach would create debug logs if something wasn't done.

The new design builds an array of language definitions which are built into constants once all of them are read.  For this reason, the new files are called *array based language files* (as opposed to the older *define based language files*).

**Note:** 1.5.8 **can** still use the old style of inclusion for non-core custom files in the older format, so older plugins and addons will run just fine without requiring modification, i.e.

```
   require 'includes/languages/english/some-custom-file.php';
```

However, if this is done:
- the file must not be overridden
- the file's definitions must be unique for the page on which they are included

If these rules are not followed, duplicate definition logs will be produced.  With this in mind, let's look at how the current system of array based language files works.

### Example

So for example, in Zen Cart 1.5.7, the file `includes/languages/english/login.php` would have: 

```
define('HEADING_TITLE', 'Welcome, Please Sign In');
```

In Zen Cart 1.5.8, the file `includes/languages/english/lang.login.php` would have: 

```
$define = [
...
    'HEADING_TITLE' => 'Welcome, Please Sign In',
... ]; 

```

with a `define` to be done later after all the strings had been gathered.

Using arrays allows for the following kinds of behavior: 

- Create a set of language definitions in the storefront override files, but run the base file to ensure that any missing definitions are created, while not updating any definitions that are changed in the override.

- Create a definition in the main language file which works for most cases, but allow it to be overridden in a per-page language file. 

In the process of doing this work, the language files were reviewed for duplicates, and consolidation was done where appropriate to reduce the burden on translators.  So some constant definitions have moved or been renamed - be sure to apply your changes and customizations with this in mind.

### Loading a language file

If you need to specifically include a **core** language file, logic that was used in Zen Cart 1.5.7 and before: 

```
  $langfile = DIR_WS_LANGUAGES . $_SESSION['language'] . '/modules/order_total/' .  'ot_group_pricing.php';
  include_once ($langfile);
```

needs to be migrated for 1.5.8 and above, because both the filename and the structure of this core file have changed.  The old file is simply not there any more, it has been migrated to `lang.ot_group_pricing.php`.

However, plugin authors may want to make their code compatible with both 1.5.7 and 1.5.8.  Here's one approach for manually loading a language file in both old and new formats, which also allows for template overrides: 

```
  $filename = 'ot_group_pricing.php'; 
  $folder = '/modules/order_total/';  // end with slash 
  $old_langfile = DIR_FS_CATALOG . DIR_WS_LANGUAGES . $_SESSION['language'] . $folder .  $filename; 
  $new_langfile = DIR_FS_CATALOG . DIR_WS_LANGUAGES . $_SESSION['language'] . $folder .  'lang.' . $filename; 
  if (file_exists($new_langfile)) {
     global $languageLoader; 
     $languageLoader->loadExtraLanguageFiles(DIR_FS_CATALOG . DIR_WS_LANGUAGES,  $_SESSION['language'], $filename, $folder); 
  } else if (file_exists($old_langfile)) {
     $tpl_old_langfile = DIR_FS_CATALOG . DIR_WS_LANGUAGES . $_SESSION['language'] . $folder .  $template_dir . '/' . $filename; 
     if (file_exists($tpl_old_langfile)) {
        $old_langfile = $tpl_old_langfile; 
     }
     include_once ($old_langfile);
  }
```

If the plugin is targeted at 1.5.8+ only, the code above can be simplified: 
```
  $filename = 'ot_group_pricing.php'; 
  $folder = '/modules/order_total/';  // end with slash 
  $new_langfile = DIR_WS_LANGUAGES . $_SESSION['language'] . $folder .  'lang.' . $filename; 
  if (file_exists($new_langfile)) {
     global $languageLoader; 
     $languageLoader->loadExtraLanguageFiles(DIR_FS_CATALOG . DIR_WS_LANGUAGES,  $_SESSION['language'], $filename, $folder); 
  }
```

If the file to be loaded was just in `includes/languages/english/` (and not the `modules/order_total` subfolder), the changes to the code above would just be for the first two variables.  To load the file `includes/languages/english/lang.media_common.php` it would be, 

```
  $filename = 'media_common.php'; 
  $folder = '/';  // end with slash 
```


If you are loading an admin side language file, you can do something like this.
Assume the file to 
be loaded is `admin/includes/languages/english/some-custom-file.php` in 1.5.7 and `admin/includes/languages/english/lang.some-custom-file.php` in 1.5.8: 

```
if (function_exists('zen_get_zcversion') && zen_get_zcversion() >= '1.5.8') { 
   $filename = 'some-custom-file.php';
   $languageLoader->loadExtraLanguageFiles( DIR_WS_LANGUAGES, $_SESSION['language'],  $filename, '/');  
} else {
   require 'includes/languages/english/some-custom-file.php'; 
}
```

### Handling back references within a file 

In Zen Cart 1.5.7 and below, structures like the following were possible: 

```
  define('TEXT_GV_NAME','Gift Certificate');
...
  define('BOX_INFORMATION_GV', TEXT_GV_NAME . ' FAQ');
```

In 1.5.8, you must create array elements which reference earlier array entries 
*after* creating the entire `$define` array. 

```
$define = [
...
    'TEXT_GV_NAME' => 'Gift Certificate',
...
]; 
$define['BOX_INFORMATION_GV'] = $define['TEXT_GV_NAME'] . ' FAQ';
```

This example is taken from `includes/languages/lang.english.php`.

### Handling back references between files 

Prior to Zen Cart 1.5.8, the `define` operations were done incrementally, so a language file which was loaded later could refer to one loaded earlier. 

For example, a file in `includes/languages/english/extra_definitions/` could do this: 
```
define('ABOUT', '<li><a href="' . zen_href_link(FILENAME_ABOUT_US) . '">' . BOX_INFORMATION_ABOUT_US . '</a></li>');
```

This is no longer permitted; the constant must be replaced by a string. 

```
define('ABOUT', '<li><a href="' . zen_href_link(FILENAME_ABOUT_US) . '">' . 'About Us' . '</a></li>');
```

{{% language_help_links %}}

