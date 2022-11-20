---
title: Upgrading plugins to work with 1.5.8/PHP 8.0+ 
description: Upgrading old Zen Cart plugins to work with Zen Cart 1.5.8
category: plugins
---

PHP8 is a major change, and many older plugins will require attention before they can be used without problems. 

## Array Based Language Files 
To avoid duplicate define notices from PHP, Zen Cart 1.5.8 uses [Array Based Language Files](/dev/code/158_language_files/).

If you need to include a language file, the old style of doing so 

```
  $langfile = DIR_WS_LANGUAGES . $_SESSION['language'] . "/modules/order_total/" .  "ot_group_pricing.php";
  include_once ($langfile);
```

will no longer work for 1.5.8 and above.  However, plugin authors may want to make their code compatible with both 1.5.7 and 1.5.8.  Here's one approach, which also allows for template overrides: 

```
  $filename = "ot_group_pricing.php"; 
  $folder = "/modules/order_total/";  // end with slash 
  $old_langfile = DIR_WS_LANGUAGES . $_SESSION['language'] . $folder .  $filename; 
  $new_langfile = DIR_WS_LANGUAGES . $_SESSION['language'] . $folder .  "lang." . $filename; 
  if (file_exists($new_langfile)) {
     global $languageLoader; 
     $languageLoader->loadExtraLanguageFiles(DIR_FS_CATALOG . DIR_WS_LANGUAGES,  $_SESSION['language'], $filename, $folder); // not $new_langfile - use base name
  } else if (file_exists($old_langfile)) {
     $tpl_old_langfile = DIR_WS_LANGUAGES . $_SESSION['language'] . $folder .  $template_dir . '/' . $filename; 
     if (file_exists($tpl_old_langfile)) {
        $old_langfile = $tpl_old_langfile; 
     }
     include_once ($old_langfile);
  }
```

On the admin side, you can do something like this: 

```
if (function_exists('zen_get_zcversion') && zen_get_zcversion() >= '1.5.8') { 
   require 'includes/languages/english/lang.ezpages.php'; 
} else {
   require 'includes/languages/english/ezpages.php'; 
}
```

If your plugin creates its own new language file, you are not required to update it; unique legacy language files will still be loaded.  See [Language Files - New and Legacy in 1.5.8](/dev/code/158_order_language_files/).

### Turning off substring match language loading 
Substring matching language loading is a feature in Zen Cart where when a page's primary language file is loaded, any other language file that starts with the page name will also be loaded.  For example, going to `index.php?main_page=video` will load legacy language file `video.php` but also any other language file whose name starts with "video". 

Due to stricter rules about `define` uniqueness, you may need to disable 
this behavior for your plugin - see [Substring Matching](/dev/code/158_order_language_files/).

### PHP 8.2 and objects 
PHP 8.2 introduces a new restriction which deprecates the use of dynamic properties.  

This means in a class, you can no longer do something like 

```
   class Foo extends base 
   {
      function __construct() {
        ...
      }
   }

   $f = new Foo(); 
   ...
   if (some-condition) { 
      $f->enabled = true;   // deprecated! 
   }
```

There are two ways to fix this: 
- Change your class to declare all their properties (class member variables) in the class definition.  You can see an example of this in `includes/modules/order_total/ot_group_pricing.php` in how the variables `$_check` and `$code` are declared with visibility explicitly in 1.5.8 but not in 1.5.7. 

For the example above, it would be 

```
   class Foo extends base 
   {
      public $enabled = false; 
      function __construct() {
        ...
      }
   }
```

- Change your class to explictly allow dynamic properties.  You can see an example of this in `admin/includes/classes/object_info.php` - the class declaration is preceded by 

```
#[AllowDynamicProperties]
```

This second method should be used sparingly and only in cases where arbitrary properties are possible (as in `objectInfo`).  If the number of properties is fixed and finite, you should simply explicitly declare them in the class.  Doing so will protect you from introducing bugs by spelling the name of a property incorrectly (this was the intention of this PHP change, after all.)

### PHP 8.2 objectInfo and plugins 

As noted above, PHP 8.2 introduces a new restriction which deprecates the use of dynamic properties.  

For core modules in admin, the `objectInfo` class has been extended to explicitly permit dynamic properties. 

Plugin developers using custom tables may extend `objectInfo` to add properties, or rely on `objectInfo`'s opt-in to dynamic properties .  The former technique is shown in the following example from [Email Archive Manager](https://www.zen-cart.com/downloads.php?do=file&id=101): 

```
  class eam_objectInfo extends objectInfo {
     public 
        $archive_id, 
        $email_to_name,
        $email_to_address,
        $email_from_name,
        $email_from_address,
        $email_subject,
        $email_html,
        $email_text; 
  }

```

Then, in the code body, instead of  

```
$email = new objectInfo($email_sql->fields);
``` 

use 

```
$email = new eam_objectInfo($email_sql->fields);
```

### PHP 8.1 and strftime 

PHP 8.1 has deprecated `strftime`.  Change calls to use the new `zcDate` class.

Before:
```
   echo strftime('%B');
```

Now:
```
   echo $zcDate->output('%B'); 
```
NB. To use inside a function or another class you will need to add 
```
   global $zcDate;
```
before you use `zcDate` for the first time.

### Related Pages

- [PHP Idioms](/dev/code/php_idioms/)
- [Release Specific Upgrade Considerations](/user/upgrading/release_specific_upgrade_considerations/)
