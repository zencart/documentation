# Documentation Standards 

Please follow these rules when adding new documentation files to the `/content/user` folder: 

- Begin each file with a block that looks like:
<pre>
---
title: "article title"
category: "article category"
weight: 1
---
</pre>

The value of `weight` denotes a sort-order. Please choose a value that makes sense given where it fits with existing articles.

- Don't use a headline starting with #.  The `title` in the block above is sufficient.

- Use backticks for denoting code and filenames.  For example `includes/classes/shopping_cart.php` should be coded as 
<pre>`includes/classes/shopping_cart.php`</pre>

- If you do need to escape an underscore outside of backticks, you can use a backslash, like this: `\_`.  
