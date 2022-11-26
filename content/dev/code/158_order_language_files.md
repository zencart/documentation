---
title: Language Files - New vs Legacy in 1.5.8+
description: How legacy language defines are handled for Zen Cart 1.5.8 and above 
weight: 10 
layout: docs
---

If you are not familiar with language files in 1.5.8, please see 
[Developer information on Array based Language files](/dev/code/158_language_files/).

For backwards compatibility with plugins, Zen Cart 1.5.8+ still 
processes older define based language files, if they are the only ones available.  This allows older plugins to work in 1.5.8.  But the new format is preferred to the old format, as explained below.

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

## Substring Matching 

Language files which are substring matches of the main language file being loaded are also loaded.  For example, if you browse to 

```
index.php?main_page=video
```

The language file `includes/languages/english/lang.video.php` is loaded (assuming it exists), and also any file matching `includes/languages/english/lang.video*.php`.

If only a legacy language file exists, then  the language file `includes/languages/english/video.php` is loaded, and also any file matching `includes/languages/english/video*.php`.

Substring matching is normally desired, but for legacy files it can cause duplicate defines, which is flagged by newer versions of PHP.  For this reason, provision for bypassing it is made in the [site specific overrides file](/user/customizing/site_specific_overrides) in 1.5.8a and above.  If you are running Zen Cart 1.5.8 but not 1.5.8a, see [PR 5397](https://github.com/zencart/zencart/pull/5397). 

{{% language_help_links %}}

