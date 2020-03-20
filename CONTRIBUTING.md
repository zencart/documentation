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
title: article title
category: article category
weight: 10
---
</pre>

The value of `weight` denotes a sort-order. Please choose a value that makes sense given where it fits with existing articles.  In most situations it makes sense to use a single value (say 10) and let alphabetic sorting be used.  If you have an article you want on top, just use a smaller sort order for that article ("About <topic> articles in `/user` do this.)

- Don't use a headline starting with #.  The `title` in the block above is sufficient.

- Use backticks for denoting code and filenames.  For example `includes/classes/shopping_cart.php` should be coded as 
`includes/classes/shopping_cart.php`

- If you do need to escape an underscore outside of backticks, you can use a backslash, like this: `\_`.  

- If you are converting an old file from the Tutorials/FAQ area, be sure to change any references to `content.php` (the old way) to a new page on the docs site. Example: 

OLD WAY: 
<pre>
Check out the &lt;a href="https://www.zen-cart.com/content.php?48-what-are-the-server-requirements-to-run-zen-cart" target="&#95;blank"&gt;Server Requirements For Running Zen Cart&lt;/a&gt;
</pre>

NEW WAY: 

<pre>
Check out the [Server Requirements for Running Zen Cart](/user/first_steps/server_requirements). 
</pre>


- Be sure to remove any references to the legacy Wiki in the same way. All content should be using the new doc site moving forward.

- If you are converting an old file from the Tutorials/FAQ area, try using an [HTML to Markdown converter](https://www.browserling.com/tools/html-to-markdown).  It may make the process faster and easier. 

- Be sure to remove the `.md` extension when creating a link.  For example do this: 

<pre>
Check out the [Server Requirements for Running Zen Cart](/user/first_steps/server_requirements).  
</pre> 

not this: 

<pre>
Check out the [Server Requirements for Running Zen Cart](/user/first_steps/server_requirements.md).  
</pre> 

- Even though the folder names are upper case, use lower case when building the link.  For example, rather than `/First_Steps/`, use `/first_steps/`, as seen in the examples above.

- For consistency, use the standard variables `YOURTEMPLATE` and `YOURLANGUAGE` where they are required (i.e. do not use underscores or another convention for identifying these things. 

- Use arrow notation for describing click paths in the Admin, rather than ellipses.  For example, use

`Configuration->EZ-Pages Settings` 

rather than 

`Configuration ... EZ-Pages Settings`.

<br /><br />

## Markdown

* [Link to Markdown Syntax](https://www.markdownguide.org/basic-syntax/)

* For simplicity, use Markdown rather than HTML on these pages where ever possible. 

* Remember that when you embed markdown within an HTML block element, markdown formatting is disabled.  To turn it back on, use a blank line before and after the markdown OR embed the content in a `<span>`.

## Cleanup of Legacy Content and Markup  

- If you see a page that contains Wiki-style (or other legacy) markup like 

`## <span class="mw-headline" id="Adding_Currencies">Adding Currencies</span>
`

please simplify it to just use Markdown markup (remove the span). 


- If you see a page that contains `FIXME`, this means the page was simply copied straight from the legacy Wiki or Tutorials area, and it should be verified against the latest Zen Cart release for accuracy.  Please edit as needed and submit a PR.



