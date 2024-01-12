---
title: Some of my PHP files are missing the PHP closing tag at the end of the file
description: Is a missing PHP closing tag an error? 
category: miscellaneous
weight: 10
---

### Symptom
The ending `?>` seems to be missing in some of my files.

With a Diff viewer I can see that in some cases the last line has changed from `?>` to `//EOF`.

### Cause
This is completely acceptable and has been done intentionally.

As you may know, if you try to run a PHP file which has whitespace (spaces or blank lines etc) after the final `?>` then it can cause problems, usually the dreaded headers already sent error.

Removing the `?>` from php files is a way of mitigating against this error. PHP will quite happily work without it (automatically assuming the closing tag at the end of the file), and thus any whitespace at the end of the file will not cause errors.

More information can be found on [this PHP.net page](http://www.php.net/basic-syntax.instruction-separation). 

### Solution
There is no special action to be taken.
This is an ongoing process that will continue into future versions of Zen Cart.

