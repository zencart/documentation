---
title: User information on Array based Language files 
description: Language Packs for Zen Cart 1.5.8 and above 
weight: 100 
layout: docs
---

In Zen Cart 1.5.8, the language file structure was modified so that the PHP `define` statement is no longer used directly.  The reason for this is that newer versions of PHP will emit warning messages when a constant is redefined, so the old approach would create debug logs if something wasn't done.

The new design builds an array of language definitions which are built into constants once all of them are read.  For this reason, the new files are called *array based language files* (as opposed to the older *define based language files*). 


If you are a developer who wants to learn how to build a new language pack, please see [Developer Information on Array based Language files](/dev/languages/158_language_files/). 

Because these new language packs are just now being built and are subject to frequent fine-tuning, the most up to date location for finding them will not be the Plugins Library, but the Github repository of the developer maintaining the library. 

### Available Array Based Language Packs for Zen Cart 1.5.8 and above

- [Spanish](https://github.com/torvista/Zen_Cart-Spanish_Language_Pack/tree/v158) 

