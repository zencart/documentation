---
title: Upgrading plugins to work with PHP8+/1.5.8+
description: Upgrading old Zen Cart plugins to work with PHP 8.x and Zen Cart 1.5.8+
category: plugins
---

PHP8 is a major change, and many older plugins will require attention before they can be used without problems.   Be sure to verify plugins in [a test environment](/user/running/local_testing/) before pushing them to a live store. 

Note: depending on the age of the plugin, you may need to do the [PHP 7 updates](/user/upgrading/php_warnings/) as well.

## Array Based Language Files 
To avoid duplicate define notices from PHP, Zen Cart 1.5.8 uses [Array Based Language Files](/dev/code/158_language_files/).

If you need to load a language file that's not already being loaded by the [default language file loading process](/dev/plugins/language_files/), see [loading a language file](/dev/code/158_language_files/#loading-a-language-file)

If your plugin creates its own new language file, you are not required to update it; unique legacy language files will still be loaded.  See [Language Files - New vs Legacy in 1.5.8](/dev/code/158_order_language_files/).

### Turning off substring match language loading 
Substring matching language loading is a feature in Zen Cart where when a page's primary language file is loaded, any other language file that starts with the page name will also be loaded.  For example, going to `index.php?main_page=video` will load language file `lang.video.php` but also any other language file whose name starts with "video" such as `lang.video_success.php`.

Due to stricter rules about `define` uniqueness, you may need to disable 
this behavior for your plugin - see [Substring Matching](/dev/code/158_order_language_files/#substring-matching).

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

Or if more arguments are used, the change is: 

Before: 
```
    $retVal = strftime(DATE_FORMAT_LONG, mktime($hour, $minute, $second, $month, $day, $year));
```

Now:
```
    $retVal = $zcDate->output(DATE_FORMAT_LONG, mktime($hour, $minute, $second, $month, $day, $year));
```


NB. To use inside a function or another class you will need to add 
```
   global $zcDate;
```
before you use `zcDate` for the first time.

### PHP 8.1 and null strings passed as parameters

If you get an error like 

```
--> PHP Deprecated: htmlspecialchars(): Passing null to parameter #1 ($string) of type string is deprecated in /admin/customers.php on line 754.
```

You would change 

```
htmlspecialchars($cInfo->street_address, ENT_COMPAT, CHARSET, true),
```

to 

```
htmlspecialchars($cInfo->street_address ?? '', ENT_COMPAT, CHARSET, true),
```


### PHP 8.2 and object properties 

If you get an error like: 

```
PHP Fatal error: Uncaught Error: Cannot access private property queryFactory::$count_queries in .../includes/classes/sitemapxml.php:735
```

This line is 
```
 $this->statisticModuleQueries = $db->count_queries;
```

There are a couple of options: 

- It may be appropriate to make the property public.  To do this, you would change `query_factory.php` from: 

```
private $count_queries = 0;
```
to
```
public $count_queries = 0;
```

- It may be appropriate to add a getter instead. Since `query_factory.php` is a core file, this is the better approach.  Change 

```
 $this->statisticModuleQueries = $db->count_queries;
```
to

```
 $this->statisticModuleQueries = $db->queryCount(); 
```

### PHP 8.0+ and missing constants 

If you get a debug log like this: 

```
[04-Aug-2023 11:50:03 UTC] PHP Fatal error:  Uncaught Error: Undefined constant "SOME_CONSTANT" in /Users/scott/Sites/gh_demo_200/...
```

please see [missing language constants](/user/localization/missing_language_constants/).


{{% code_help_links %}} 

