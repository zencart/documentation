---
title: 'Parse error:  unexpected T_STRING (or similar)'
description:  How do I resolve this PHP message? 
category: troubleshooting
weight: 10
---

If you are getting an error similar to:

```
"Parse error: parse error, unexpected T_STRING in /var/www/myaccount/public_html/includes/languages/english/SOMETHING.php on line 28"
```

This typically means you have forgotten to put a `\` (backslash) before a `'` mark (single quote, apostrophe) in one of your `define()` statements in the language file reported.

Example:

```
define('TEXT_SOMETHING','This is something simple that\'s used as an example');
```

(notice the `\` in the word `that's`).

