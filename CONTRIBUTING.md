# Contributing to Zen Cart Documentation 

Thanks for contributing to the Zen Cart documentation!  

The intention is for documentation in this repository to replace the 
legacy Wiki and FAQs/Tutorials page on zen-cart.com. 

## Getting Started 
To get started, follow the guidelines in the project's README file 
for cloning and setting up the repo and running `Hugo` locally. 

Submit your changes as Pull Requests, following the documentation standards
provided below.  

## Documentation Standards 

Please follow these rules when adding new documentation files to the `/content/user` and `/content/dev` folders: 

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
