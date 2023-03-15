---
title: 'Warning: Headers already sent...'
description: Fixing this PHP warning message 
category: troubleshooting
weight: 10
---

**Symptom:**  

```
Warning: Cannot modify header information - headers already sent by (output started at /..../includes/something/something/something.php:12) in ..../includes/something_else.php on line 67  
```

**Common Cause:**

This warning is often caused by a blank space or extra line at the beginning or end of a .php file.  
Check the error for the filename that generated the error (ie: the "output started at...." filename), open that file in your text editor and remove the extra spaces or lines immediately <u>before the first</u> **`<?php`** marks in the file, <u>or after the</u> closing **`?>`**  

**<u>Other Causes: Syntax errors</u>**  

In the example above, you'll see 

```
output started at includes/something/something/something.php:12
```

The filename in the message above is the file you need to be concerned about. 
The number after the filename is the line that caused the problem.  For example, `12` means that the problem you need to fix is on line 12.  In that same example, 
```
includes/something_else.php on line 67
```

<u>can be completely ignored</u>. It is not the problem. It is the one that discovered that the problem had already occurred.  

If the "headers already sent" error appears AFTER any other error, then you need to fix that other error FIRST. (The error message itself is what caused headers to be sent, so fixing that error will cause the second error to go away too.)  

If the "started at" refers to line 1, then the root cause is one of two things: 

- a space (possibly a blank line) before the opening **&lt;?php** tag or 
- **incorrect encoding** on the file.  

Remember, if your language is in UTF8, then you MUST encode the file as "UTF8-without-BOM", else the BOM (byte-order-mark, an invisible character at the beginning of the file) will cause this same headers-already-sent error.  

**Summary:**  

a) look for where it 'started at'  
b) track the line number  
c) check what's normally happening on that line.  

- If it's the end of the file, and there is a `?>` at the end of the file, remove the final `?>`. 
- If it's the start of the file, the issue is likely spaces or incorrect encoding.  
- If it's elsewhere, it could be a syntax error or the result of an `echo()` statement which is displaying info or perhaps debug code.  
- Common syntax errors include the use of single-quotes inside statements that already have single-quotes. Check to be sure your quotes aren't mismatched. If you need to use single-quotes while inside other single-quotes, change yours to `\'` instead of just `'`.  

d) the rest of the info simply shows other execution information, mainly the part of the code that discovered that it cannot proceed as expected due to the problem that happened in the 'started at' location.  

To change the encoding on the file, look for the "Save As" menu item in your
[text editor](/user/first_steps/useful_tools/#php-html-and-text-editors).

The utility [Find Extra Spaces](https://github.com/torvista/Zen_Cart-Find_Extra_Spaces) may be helpful in tracking down issues like this.  

