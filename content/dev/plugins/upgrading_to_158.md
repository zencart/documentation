---
title: Upgrading plugins to work with 1.5.8/PHP 8.0+ 
description: Upgrading old Zen Cart plugins to work with Zen Cart 1.5.8
category: plugins
---

## Array Based Language Files 
To avoid duplicate define notices from PHP, Zen Cart 1.5.8 uses [Array Based Language Files](/dev/languages/158_language_files/).

If you need to include a language file, the old style of doing so 

```
  $langfile = DIR_WS_LANGUAGES . $_SESSION['language'] . "/modules/order_total/" .  "ot_group_pricing.php";
  include_once ($langfile);
```

will no longer work for 1.5.8 and above.  However, plugin authors may want to make their code compatible with both 1.5.7 and 1.5.8.  Here's one approach: 

```
  $filename = "ot_group_pricing.php"; 
  $old_langfile = DIR_WS_LANGUAGES . $_SESSION['language'] . "/modules/order_total/" .  $filename; 
  $new_langfile = DIR_WS_LANGUAGES . $_SESSION['language'] . "/modules/order_total/" .  "lang." . $filename; 
  if (file_exists($old_langfile)) {
          include_once ($old_langfile);
  } else if (file_exists($new_langfile)) {
     global $languageLoader; 
     $folder = "/modules/order_total/"; 
     $languageLoader->loadExtraLanguageFiles(DIR_FS_CATALOG . DIR_WS_LANGUAGES,  $_SESSION['language'], $filename, $folder);
  }
```

### PHP 8.2 objectInfo and plugins 

PHP 8.2 introduces a new restriction which deprecates the use of dynamic properties.  For core modules in admin, the `objectInfo` class has been extended to contain all possible data elements (based on the creation of an instance from a query result).  Plugin developers using custom tables (or even references to built-in tables which are not used by other core modules) should simply extend `objectInfo`.  Consider the following example from Email Archive Manager: 

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

