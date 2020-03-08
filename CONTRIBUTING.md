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

- If you are converting an old file from the Tutorials/FAQ area, be sure to change any references to content.php (the old way) to a new page on the docs site. Example: 

OLD WAY: 
<pre>
Check out the &lt;a href="https://www.zen-cart.com/content.php?48-what-are-the-server-requirements-to-run-zen-cart" target="&#95;blank"&gt;Server Requirements For Running Zen Cart&lt;/a&gt;
</pre>

NEW WAY: 

<pre>
Check out the &lt;a href="/user/First_Steps/server_requirements.md" target="&#95;blank"&gt;Server Requirements For Running Zen Cart&lt;/a&gt;
</pre>

- Be sure to remove any references to the legacy Wiki in the same way. 

- If you are converting an old file from the Tutorials/FAQ area, try using an [HTML to Markdown converter](https://www.browserling.com/tools/html-to-markdown).  It may make the process faster and easier. 
