# Contributing to Zen Cart Documentation 

Thanks for contributing to the Zen Cart documentation!  

The intention is for documentation in this repository to replace the 
legacy Wiki and FAQs/Tutorials page on zen-cart.com. 

## Getting Started 
To get started, follow the guidelines in the project's README file 
for cloning and setting up the repo and running `Hugo` locally. 

Submit your changes as Pull Requests, following the guidelines 
provided below.  

## Content Recommendations 

Structure your writing to explain current operation and *then* (if necessary and relevant) past history. 

In other words, don't say "we don't do it the old way anymore, and first let us explain the old way."

## Documentation Standards 

Please follow these rules when adding new documentation files to the `/content/user` and `/content/dev` folders: 

- Begin each file with a block that looks like:
<pre>
---
title: article title
description: article description 
category: article category
weight: 10
---
</pre>

- The title will be shown on the page, but the description will only be used in the description meta tag, so say "Zen Cart" somewhere in the description.  

- The value of `weight` denotes a sort-order. Within folders, please set as follows: 

    - Use `weight: 10` as the default. This way alphabetic sorting will be used for most content, which is what is desired.

    - Use `weight: -1` for the first article in a folder (generally a "Using &lt;subsystem&gt;" or "About &lt;subsystem&gt;" type article). 
    
    - There are a few exceptions to this rule, such as Release History (sorted in reverse chronological order) and Admin Pages (sorted in the order they appear in Zen Admin), but for the most part, this rule is followed.

- Don't use a headline starting with #.  The `title` in the block above is sufficient.

- Use backticks for denoting code and filenames.  For example, the filename "includes/classes/shopping\_cart.php" should be coded as 
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


- For consistency, use these standard names:
    - `YOURSITE` - your domain name 
    - `YOURTEMPLATE` - your template name 
    - `YOURLANGUAGE` - your language (/english/ by default)
    - `YOURACCOUNTFOLDER` - your home folder provided by your hoster
    - `YOURSUBFOLDER` - if your site is below webroot   
    
    For details see the article [Basic Terms](user/new_user_topics/basic_terms). 

    **Please DO NOT use any other convention** like `/YOUR_CUSTOM_TEMPLATE/`, `/YOUR_STORE/`, `YOURSTORE`, `/your_site/`, `/custom/` , etc. - use the standard names above. 


- Use a space padded greater than sign (` > `) for describing click paths in the Admin, rather than ellipses.  For example, use this: 

`Configuration > EZ-Pages Settings` 

NOT THIS:  

`Configuration ... EZ-Pages Settings`              **NO!** 

NOT THIS:  

`Configuration->EZ-Pages Settings`              **NO!** 


## Links 

- Use relative paths, starting with the folder under `/content`,  so people can test their changes locally.  Use this: 

`[Github Workflow](/dev/contributing/github_workflow/)`

NOT THIS:

`[Github Workflow](https://docs.zen-cart.com/dev/contributing/github_workflow/)`       **NO!** 

NOT THIS: 
`[Github Workflow](github_workflow/)`       **NO!** 

- Cross-link liberally!  Example: 

`See [FTP tools](/user/first_steps/useful_tools/#ftp-tools) for a list ...`

but use the built in `id` tags which are created by headers of all levels.
So do this: 

```
FILE 1:
See [What does MIXED ON mean?](/user/products/using_products#what-does-mixed-on-mean)
```

```
FILE 2:
### What does MIXED ON mean? 
```

NOT THIS:

```
FILE 1:
See [What does MIXED ON mean?](/user/products/using_products#mixed) **NO!** 
```

```
FILE 2:
<div id="mixed"></div>.  **NO!**

**What does MIXED ON mean?**
```




<br />

## Markdown

* [Link to Markdown Syntax](https://www.markdownguide.org/basic-syntax/)

* For simplicity, use Markdown rather than HTML on these pages where ever possible. But remember that **when you embed markdown within an HTML block element, markdown formatting is disabled**.  To turn it back on, use a blank line before and after the markdown OR embed the content in a `<span>`.

* To embed an image, put the image in `/content/images` and use the `img` tag to display it: 

```
<img src="/images/version_link.png" alt="Zen Cart Version information" />
```

* If you are using the same text in multiple places, please don't copy and paste; instead, use a shortcode or modify a template.  This is an advanced area; please ask first.  Alternately, you can simply link to the content in the main place it exists. See the section *Links* above. 

* Exercise caution when changing a header (a line preceded by one or more # signs).  The reason is that the text of this header is a link which is used to crosslink.  So if you have 

```
### Header One 
```


The link to this would be `[See Header One](/user/folder/file#header-one)`.  And if you change the "Header One" to something else, this link will no longer work! 

<br />

## CSS
There are two CSS files you can modify: 

- `assets/scss/_variables_project.scss` - loaded BEFORE the template CSS
- `assets/scss/_styles_project.scss` - loaded AFTER the template CSS

The former is appropriate for defining styles which are not part of 
the template; the latter is appropriate for modifying styles which are 
part of the template. 

When you change these files, you must restart `hugo server`; they are not rebuilt the way content files are. 

<br />


## Cleanup of Legacy Content and Markup  

- If you see a page that contains Wiki-style (or other legacy) markup like 

`## <span class="mw-headline" id="Adding_Currencies">Adding Currencies</span>`

please simplify it to just use Markdown markup (remove the span). 

`## Adding Currencies`

<br />

## Notes for the Future

- If there's a bug in the content that you just don't have time to fix, mark it with a visible `FIXME` so a future maintainer (maybe you!) will notice it and take care of it. 

```
FIXME - clarify the difference between foo and bar.
```

- If there's content that needs to be revisited at every release, mark it with a hidden `RELEASETIME` so people can quickly find content that needs refreshing. 

```
<!-- RELEASETIME - be sure this still applies --> 
```


## Developer Docs 
Some folders under `/content` contain a file called `developers_read_me.txt`.  These files contain instructions on how to manage program-generated content, such as the configuration page help files. 

See also the Github repo https://github.com/scottcwilson/zencart_tools



