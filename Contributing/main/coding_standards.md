#Coding Standards
-----------------
## Old Standard
Legacy code has used a modified phpBB coding style, with notable characteristics such as "indent with 2 spaces, not tabs", "The opening brace for class and function definitions, as well as if/else statements, was kept on the same line", etc.

## New Standard: PSR-2
In the interest of progressively modernizing the code, going forward we are adopting the PSR-2 coding standard (which also includes PSR-1 standards).

##When to use PSR-2
So, new code should use the PSR-2 standard. That is, when new files are created such as new functions or class files, they should use the PSR-2 standard.

##When to use old style
When doing maintenance to existing code in existing files, and to some degree when adding code to existing files, the format of those files should not be radically changed. 

Reasons: difficulty for people upgrading since they need familiar comparison points to merge changes, and familiarity for those working in those files ... it's better for there to be one style per file.

##When to reformat an entire file
If a file needs reformatting, that reformatting should be a SEPARATE commit (and preferably separate Pull Request) from ANY other changes.  ie: there should be no functionality changes, no changes to the file other than white-space.

This is for the purpose of maintainability, and controlling understanding of the flow of code changes ... especially important if a bug is later found in the code.

##Comments in Code

It is appropriate to use comments to explain what is happening in a given section of the code. This is so that other programmers coming after you (and you included!) can quickly understand intended the logic.

Standard phpDocumentor coding standards are the preferred approach, as well as inline comments approximately every 10 lines of code. 


## What about files containing both HTML and PHP?
Where possible, (new) code should always output HTML/CSS/JS directly, and NOT use PHP to echo the HTML.

Code-editing programs can understand the HTML and PHP distinctly if the HTML/CSS/JS are "raw text".  So, it becomes problematic if HTML is "echoed" via PHP.

Examples:

###Good:
```html
<div class="xxxxxx"><?php echo sprintf(LANGUAGE_DEFINE, ...); ?></div>
```

###Bad:
```php
<?php echo ' <div class=xxxxxx">' . sprintf(LANGUAGE_DEFINE, ...) . '</div>'; ?>
```
