---
title: PHP Idioms 
description: Coding practices you will see in recent versions of Zen Cart
category: code
weight: 10
---

This document is intended to capture PHP changes that some developers may find unclear because they differ from what was done in the past.  Some but not all are driven by PHP8 changes.  

## Identical comparison operator 

The comparison operator `===` means "equal to and of the same type."  It has become more important in PHP8+, which does stricter comparisons.  

See the PHP documentation on [Comparison Operators](https://www.php.net/manual/en/language.operators.comparison.php) for more details. 

## Null coalescing operator 

This null coalescing operator `??` checks that the first operand exists and is not null.  If so, it returns the first  operand; otherwise, it returns the second operand.

So 

```
$enddate = zen_db_input($_REQUEST['end_date'] ?? date('Y-m-d'));
```

is the same as: 

```
if (!empty($_REQUEST['end_date'])) { 
   $enddate = zen_db_input($_REQUEST['end_date']); 
} else {
   $enddate = date('Y-m-d');
}
```
 

See the PHP documentation on [Null coalescing operator](https://www.php.net/manual/en/migration70.new-features.php#migration70.new-features.null-coalesce-op) for more details. 


## Missing PHP close tag `?>` at the end of a file 

The close tag `?>` is not recommended at the end of a file, and should be left off. 

{{% code_help_links %}} 
