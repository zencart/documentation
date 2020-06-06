NOTE: This document is a work-in-progress...

Interception

- a notifier at the start to completely change the defined css-js handler if one wishes to completely bypass the built-in one

BODY Classes

- BODY classes dynamically added based on page-name, current-product-id, current-mfg-id, current-category-id, current-cPath, current-language
 ... and a notifier to allow complete alteration/override of all those

Framework injected css, js

- notifier to set which CSS framework is in use (in case elsewhere something needs to be set based on the named framework)

Stylesheet files
Stylesheet filenames are loaded in this order, if present:

 1. all stylesheets for your selected CSS framework, or whatever were set via the notifier hook (if any), followed by:

 2. stylesheet.css

 3. stylesheet-responsive.css

 4. font.css

 5. inline_en_stylesheet.css

 6. inline_pagename.css

 7. inline_en_pagename.css

 8. inline_c_cpath.css

 9. inline_en_c_cPath.css

 10. inline_m_mfgId.css

 11. inline_en_m_mfgId.css

 12. inline_p_productId.css

 13. inline_en_p_productId.css

 14. print\*.css
 
De-duplication is done to ensure duplicates/conflicts are managed when the framework dictates certain files, and the template has same files.

CSS `<link>` tags are assigned an `id` so that javascripts can enable/disable them if necessary.

_It is generally advisable to avoid using inline-styling wherever possible; however, due to popular demand for maximum flexibility, this is included for granular control at the per-page and per-feature level._

JS files

- jscript_top_xxxx.php and jscript_top_xxxxx.js files are loaded at the top of the page (in HEAD)
- other jscript_xxxxx.php and jscript_xxxxx.js files are loaded at the bottom of the page (below footer) to prevent blocking
- De-duplication is done to ensure duplicates/conflicts are managed when the framework dictates certain files, and the template has same files.

