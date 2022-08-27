---
title: Coding Standards
description: Formatting and Coding Best Practices 
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

Guidelines on reformats: 

**PLEASE use restraint in deciding when a reformat is truly required.** Reformats cause unskilled storeowners grief when they go to upgrade, and use up limited core committer time while not fixing bugs.

- Please do not reformat files unless they  have already been changed for functional reasons within a release.  
- Reformatting should be done with phpStorm set to PSR-12 standards.  See [this StackOverflow post](https://stackoverflow.com/questions/57475642/phpstorm-and-psr-12-how-can-i-add-it-as-default-coding-style). 

---

# Additional Guidelines 

## Require and Include statements 

When doing a `require` or `include`, use single quotes and no parentheses. 

```
require DIR_WS_INCLUDES . 'footer.php';
```

## Quotation marks 

Remember that double quoted strings are checked for interpolation.  

Use single quoted strings in cases where variables are not used.  If single and double quotes are used within a string, use single quotes on the outside.

```
echo 'Token set. You may now continue configuring the module.'; 
```

By convention, MySQL statements are enclosed in double quotes so that values may be entered in single quotes (without interpolation).  See below. 

## MySQL Statements

MySQL keywords should be entered in uppercase.

Strings should be double quoted so that values may be single quoted. 

```
$db->Execute("INSERT INTO " . TABLE_TAX_CLASS . " 
              (tax_class_title, tax_class_description, date_added)
              VALUES ('" . zen_db_input($tax_class_title) . "',
                      '" . zen_db_input($tax_class_description) . "',
                      now())");
```

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

Note that this rule is not required in cases where a block is opened by PHP (as in `zen_draw_form`).  In this case, closing the block in straight HTML will confuse IDEs.

### Exception: 

```
        echo zen_draw_form('customers', FILENAME_CUSTOMERS, .... 
        ...
        <?php echo '</form>'; ?>
```

## Arrays 

End an array with a comma and put the closing bracket on a new line.  In this way, plugin authors can just insert a line after the last entry and have a smaller diff: 

```
[
   'class' => $totals->fields['class'],
   'value' => $totals->fields['value'],
];
```


## Separating content, markup and logic 
Where possible, try to keep these things separate:

- Files in `includes/languages` should contain strings (not HTML/CSS markup);
- Files in `includes/modules` and `includes/functions` should be where logic resides (not markup);  
- Files in `includes/templates` should be where display markup resides (not extensive logic).

## Static Data 
Try to avoid creating db tables that are strictly static data, unless they're useful in query joins with other relational data.  Keep this information in code files instead. If it needs to be globally available, use `extra_configures`.

## Namespaced Autoloading
In Zen Cart 1.5.7 some code is now using the [PSR-4 autoloading standard](https://www.php-fig.org/psr/psr-4/) for handling code in the \ZenCart namespace (ie: the files in `/includes/library`).

## Parameters 
Instead of just passing a boolean value, consider naming  the parameter for greater clarify. 

Rather than this: 
```
   $filter = zen_get_linked_products_for_category($cat_id, true); 
```

Do this: 
```
   $filter = zen_get_linked_products_for_category($cat_id, $first_only = true); 
```

## Facilitating Future Changes 

Structure your code so that future changes create smaller diffs.  So for example, 

- When creating an array, put each entry on a new line followed by a comma (even the last one).  That way someone can just add a new entry on a new line if a new entry is needed.
- Don't put large complex blocks of logic on a single line.  Don't do this, for example: 
```
        $lc_text = '<h3 class="itemTitle"><a href="' . zen_href_link(zen_get_info_page($listing->fields['products_id']), 'cPath=' . (($_GET['manufacturers_id'] > 0 and $_GET['filter_id'] > 0) ?  zen_get_generated_category_path_rev($_GET['filter_id']) : ($_GET['cPath'] > 0 ? zen_get_generated_category_path_rev($_GET['cPath']) : zen_get_generated_category_path_rev($listing->fields['master_categories_id']))) . '&products_id=' . $listing->fields['products_id']) . '">' . $listing->fields['products_name'] . '</a></h3><div class="listingDescription">' . zen_trunc_string(zen_clean_html(stripslashes(zen_get_products_description($listing->fields['products_id'], $_SESSION['languages_id']))), PRODUCT_LIST_DESCRIPTION) . '</div>';
```
- Don't put php close tags on the same line as code unless the open tag is also on that line.  Rather than this: 
```
} else { echo "foo"; } ?>
```

use this:
```
} else { 
  echo "foo"; 
} 
?>
```

## Strict comparisons 
Unless data is coming in from an external source (such as a payment module), strict comparisons are preferred. 

Rather than this: 

```
   if ($boolean_variable) {  
```

If possible, do this: 

```
   if ($boolean_variable === true) {  
```

## PHP Short Echo Tags 
At this time, PHP Short Echo Tags (`<?=` in lieu of `<?php echo`) are not preferred. 

## More Information
More information is provided in [PHP Idioms](/dev/code/php_idioms/).

