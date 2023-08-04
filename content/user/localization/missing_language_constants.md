---
title: Missing Language Constants
description: Fixing a missing language define in translated language packs
category: localization
weight: 10
---

**NOTE:** These instructions are for Zen Cart 1.5.8 and above.  

If you are running under PHP 8.0 or higher, a missing language definition will cause a blank screen.  This is a particular risk for translated language packs, which might not be up to date with the latest Zen Cart version, but it can also happen for plugins with out of date or incomplete language files. 

The [debug log](/user/troubleshooting/debug_logs/) will start with a message like this: 

```
[04-Aug-2023 11:50:03 UTC] PHP Fatal error:  Uncaught Error: Undefined constant "SOME_CONSTANT" in /Users/scott/Sites/gh_demo_200/...
```

To fix this issue, follow these steps: 

- Locate the language constant in English, looking first in `includes/languages/lang.english.php`, then under `includes/languages/english`. 
- When you have found the English language definition, update the file in the version for `YOURLANGUAGE` to add the definition.  For example: 
   - If the definition is in `includes/languages/lang.english.php`, update `includes/languages/lang.YOURLANGUAGE.php`
   - If the definition is in `includes/languages/english/lang.index.php`, update `includes/languages/YOURLANGUAGE/lang.index.php`
  

{{% language_help_links %}}
