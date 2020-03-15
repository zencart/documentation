---
title: Warning Headers already sent...
category: troubleshooting
weight: 1
---

**Symptom:**  

Warning: Cannot modify header information - headers already sent by (output started at /..../includes/something/something/something.php:12) in ..../includes/something_else.php on line 67  

*Common Cause:*
This warning is often caused by a blank space or extra line at the beginning or end of a .php file.  
Check the error for the filename that generated the error (ie: the "output started at...." filename), open that file in your text editor and remove the extra spaces or lines immediately <u>before the first</u> **<?php** marks in the file, <u>or after the</u> closing **?>**  

**<u>Other Causes: Syntax errors</u>**  
In the example above, you'll see 
<pre>
output started at includes/something/something/something.php:12</font>.
</pre>

The filename in the message above is the file you need to be concerned about. 
The number after the filename is the line that caused the problem.  For example, `12` means that the problem you need to fix is on line 12.  In that same example, 
<pre>
includes/something_else.php on line 67
</pre> 
<u>can be completely ignored</u>.</font> It is not the problem. It is the one that discovered that the problem had already occurred.  

If the "headers already sent" error appears AFTER any other error, then you need to fix that other error FIRST. (The error message itself is what caused headers to be sent, so fixing that error will cause the second error to go away too.)  

If the "started at" refers to line 1, then it's either a space before the opening **<?php** tag or it's **incorrect encoding** on the file.  

Remember, if your language is in UTF8, then you MUST encode the file as "UTF8-without-BOM", else the BOM (byte-order-mark, an invisible character at the beginning of the file) will cause this same headers-already-sent error.  

**Summary:**  

a) look for where it 'started at'  
b) track the line number  
c) check what's normally happening on that line.  
--- If it's the end of the file, then it's blank spaces.  
--- If it's the start of the file, it's likely spaces or incorrect encoding.  
--- Elsewhere it could be a syntax error or the result of an "echo()" statement which is displaying info or perhaps debug code.  
--- Common syntax errors include the use of single-quotes inside statements that already have single-quotes. Check to be sure your quotes aren't mismatched. If you need to use single-quotes while inside other single-quotes, change yours to \' instead of just '.  
d) the rest of the info simply shows other execution information, mainly the part of the code that discovered that it cannot proceed as expected due to the problem that happened in the 'started at' location.  

To change the encoding on the file, look at your editor's "save as" menu, or the program's preferences settings. A good editor to use is [Notepad++](http://notepad-plus-plus.org). 
