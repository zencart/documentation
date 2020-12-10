---
title: How do I build HTML-formatted Email for other languages?
description: Multilanguage HTML email 
category: email
weight: 10
---

The HTML emails are built from the structure of the template files in the `/email` folder. These are normally used for all languages.
However, you may create/use language-specific templates in subfolders named in accordance with the 2-letter language code.

ie:

*   /email/de/
*   /email/es/
*   /email/fr/

A template in a language folder will be used for that language in preference to the `/email` folder. It is not necessary to replicate all the templates from the `/email` folder, only those you wish to format differently. 
