---
title: Language Files - New and Legacy in 1.5.8+
description: How legacy language defines are handled for Zen Cart 1.5.8 and above 
weight: 10 
layout: docs
---

If you are not familiar with language files in 1.5.8, please see 
[Developer information on Array based Language files](/dev/code/158_language_files/).

For backwards compatibility with plugins, Zen Cart 1.5.8+ still 
processes older define based language files, if they are the only ones available.  This allows older plugins to work in 1.5.8.

### Storefront: 
- The main language file is `includes/languages/lang.english.php`.  
- This file may be overridden as `includes/languages/YOURTEMPLATE/lang.english.php`.  
- Each page has its own language file, `includes/languages/english/lang.PAGENAME.php`.  
- This file may be overridden as `includes/languages/english/YOURTEMPLATE/lang.PAGENAME.php`.
- If the above page specific files do not exist, the system checks for an older define based file, `includes/languages/english/YOURTEMPLATE/PAGENAME.php` and `includes/languages/english/PAGENAME.php`. 

If both older and newer style files exist, the older files are ignored. 

Example: 

If both 

```
./includes/languages/english/lang.order_status.php
./includes/languages/english/order_status.php
```
exist, the second one (the older style define based file) is ignored.

### Admin: 
- The main language file is `admin/includes/languages/lang.english.php`.  
- Each page has its own language file, `admin/includes/languages/english/lang.PAGENAME.php`.
- If the page specific file does not exist, the system checks for an older define based file, `admin/includes/languages/english/PAGENAME.php`. 

Again, if both older and newer style files exist, the older files are ignored. 

### Related: 
- [Developer information on Array based Language files](/dev/code/158_language_files/)
- [User information on Array based Language files](/user/localization/158_language_files/)
- [Creating a Language Pack for Zen Cart 1.5.8 and above](/dev/languages/creating_a_language_pack/) 

