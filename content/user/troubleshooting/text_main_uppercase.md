---
title: I've got TEXT_MAIN being displayed on my page
description: Unexpected uppercase words showing in page content or error logs
category: troubleshooting 
weight: 10
---

An uppercase set of words akin to `TEXT_MAIN` or `ENTRY_STATE_TEXT`  or `SOMETHING_LOOKING_LIKE_THIS`  is called a "constant" in PHP language terms.
A PHP `define()` statement is used to declare a constant.

This is what Zen Cart currently uses to build language output content, among other things.

Commonly you'll see language definitions in the form of:

```
define('TEXT_MAIN', 'Something to display here');
```

Then, in a template file or somewhere else in the system, there will be a request to display the contents of `TEXT_MAIN`, often in a PHP "echo" statement, but could be in many other forms too.

If the constant `TEXT_MAIN` hasn't been defined anywhere, or if the file in which it is defined has a syntax error above where it's defined (causing it to not *get* defined), then the name of the constant will be displayed *instead of* the defined content.

If you're seeing `TEXT_MAIN` on your screen instead of regular normal language words, then *somewhere* in your files is a request to display the value defined to the `TEXT_MAIN` constant, but, since you don't have it defined, you're seeing the constant name instead.

You have to find out where it was supposed to be defined, and fix it.

80% of the time this is a cause of someone editing a language file and "deleting" define statements that they don't want to display, instead of just deleting the text that's currently being displayed.
ie: instead of just deleting the line altogether if they don't like what TEXT_MAIN was defined to in the first place, one should use something like this to make it display "nothing":

```
define('TEXT_MAIN', '');
```

10% of the time it's a result of a syntax error where a define statement earlier in the file has mismatched quotation marks, or a `)` or `;` has been dropped.

10% of the time it's because you've failed to upload the language file altogether, and thus the define is missing.

You might start with checking which files you've edited recently or plugins you've added, or compare your files vs a fresh set of Zen Cart files.

