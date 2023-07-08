---
title: Language Files - User information on Array based Language files 
description: Language Packs for Zen Cart 1.5.8 and above 
weight: 10 
layout: docs
---

In Zen Cart 1.5.8, the language file structure was modified so that the PHP `define` statement is no longer used directly.  The reason for this is that newer versions of PHP will emit warning messages when a constant is redefined, so the old approach would create debug logs if something wasn't done.

The new design builds an array of language definitions which are built into constants once all of them are read.  For this reason, the new files are called *array based language files* (as opposed to the older *define based language files*). 


If you are a developer who wants to learn how to build a new language pack, please see [Developer Information on Array based Language files](/dev/code/158_language_files/). 

If you're doing an upgrade and are worried about all the language file changes you'll have to figure out, a better way forward is to start small and add customizations as they are needed.  Many older templates made unnecessary changes which you will not want to carry forward.  See [basic 158+ language file customizations](/user/localization/basic_158_language_customizations/).

Because these new language packs are just now being built and are subject to frequent fine-tuning, the most up to date location for finding them will not be the Plugins Library, but the Github repository of the developer maintaining the library. 

### Available Array Based Language Packs for Zen Cart 1.5.8 and above

Please see [Updated Language Packs](/user/localization/updated_language_packs/). 

{{% language_help_links %}}

