---
title: Language File Loading Conventions 
description: Which language files are loaded for my plugin? 
category: plugins
weight: 10
---

If a storefront side plugin creates a new page 

`index.php?main_page=newpage`

It will be able to use language definitions from the following files, which will be automatically loaded: 

- the main language file `includes/languages/lang.english.php` and the templated version of that file, `includes/languages/YOURTEMPLATE/lang.english.php`. 

- files in `includes/languages/english/extra_definitions` (and their templated versions)

- The page's own language file, `includes/languages/english/lang.newpage.php` 

- Language files which are a substring match of the name of the main file - for example, `includes/languages/english/lang.newpage_process.php` and `includes/languages/english/lang.newpage_success.php`.  Note that this behavior may be disabled for specific files - see [substring matching for language files](/dev/code/158_order_language_files/#substring-matching).

If you need to load a language file that's not loaded by these conventions, follow the instructions in [loading a language file](/dev/code/158_language_files/#loading-a-language-file). 

