---
title: Coding Standards
description: Zen Cart Coding Standards
weight: 2
---

## Old Standard
Legacy Zen Cart code has used a modified *phpBB* coding style, with notable characteristics such as "indent with 2 spaces, not tabs", and "The opening brace (ie: `{`) for `class` and `function` definitions, as well as `if/else` statements, was kept on the same line", etc.

## New Standard: PSR-2
In the interest of progressively modernizing the code, going forward we are adopting [the PSR-2 coding standard](https://www.php-fig.org/psr/psr-2/), which also includes PSR-1 standards.

### Difference from the "Old Standard"
To be clear: PSR-2 uses "4 spaces instead of tabs", and puts the opening `{` braces on a new line when used with `class` and `function` declarations (but keeps them on the same line when used with controls structures such as `if`, `for`, `foreach`, `switch` or `while` loops.)

For example, the old style would be:

```php
class foo extends baz {
  function bar() {
    if ($var1 == $var2) {
      // do something
    }
    return;
  }
}
```

and the new PSR-2 equivalent would be:

```php
class foo extends baz
{
    function bar() 
    {
        if ($var1 == $var2) {
            // do something
        }
        return;
    }
}
```

## When to use PSR-2
So, new code should use the PSR-2 standard. That is, when new files are created such as new functions or class files, they should use the PSR-2 standard.

## When to use old style
When doing maintenance to existing code in existing files, and to some degree when adding code to existing files, the format of those files should not be radically changed. 

Reasons: difficulty for people upgrading since they need familiar comparison points to merge changes, and familiarity for those working in those files ... it's better for there to be one style per file.

## When to reformat an entire file
If a file needs reformatting, that reformatting should be a SEPARATE commit (and preferably separate Pull Request) from ANY other changes.  ie: there should be no functionality changes, no changes to the file other than white-space.

This is for the purpose of maintainability, and controlling understanding of the flow of code changes ... especially important if a bug is later found in the code.

## Comments in Code

It is appropriate to use comments to explain what is happening in a given section of the code. This is so that other programmers coming after you (and you included!) can quickly understand intended the logic.

The standard phpDocumentor coding standard (ie: common PHP DocBlock syntax) is the preferred approach, as well as inline comments approximately every 10 lines of code. 


## What about files containing both HTML and PHP?
Where possible, (new) code should always output HTML/CSS/JS directly, and NOT use PHP to echo the HTML.

Code-editing programs can properly parse and display HTML/CSS/JS if they are entered in "raw text" - but they can't if they are "echoed" via PHP.

Examples:

### Good:
```html
<div class="xxxxxx"><?php echo sprintf(LANGUAGE_DEFINE, ...); ?></div>
```

### Bad:
```php
<?php echo ' <div class=xxxxxx">' . sprintf(LANGUAGE_DEFINE, ...) . '</div>'; ?>
```
## Separating content, markup and logic 
Where possible, try to keep these things separate:
- Files in `includes/languages` should contain strings (not HTML/CSS markup);
- Files in `includes/modules` and `includes/functions` should be where logic resides (not markup);  
- Files in `includes/templates` should be where display markup resides (not extensive logic).

## Namespaced Autoloading
In Zen Cart 1.6.0, the [PSR-4 autoloading standard](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader) is used for handling code in the \ZenCart namespace (ie: the files in `/includes/library`).

