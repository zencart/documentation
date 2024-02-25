# Contributing to Zen Cart Documentation 

Thanks for contributing to the Zen Cart documentation!  

The intention is for documentation in this repository to replace the legacy Wiki and FAQs/Tutorials page on zen-cart.com. 

## Getting Started 
To get started, follow the guidelines in the project's README file for cloning and setting up the repo and running `Hugo` locally. 

Submit your changes as Pull Requests (PRs), following the guidelines provided below.  

## PR content 

- Keep PRs to a single theme; don't submit a basket of unrelated changes.  This allows for easier merges.

- When your PR is submitted, you will get a preview build so you can see what it looks like. 

<img alt="PR Preview" src="https://github.com/zencart/documentation/blob/master/content/images/pr_preview.png" />

Click that link and find the page(s) that show your preview, then include them in a PR comment.  For example, if you have changed 

```
https://docs.zen-cart.com/user/first_steps/server_requirements/
```

then your preview URL will look like this: 

```
https://deploy-preview-NNN--zencartdocs.netlify.app/user/first_steps/server_requirements/
```

where `NNN` is your PR number.


This makes it much faster for the core committers to review your work and get it merged. 


## Content Recommendations 

Structure your writing to explain current operation and *then* (if necessary and relevant) past history. 

In other words, don't say, "we don't do it the old way anymore, and first let us explain the old way."

A phrasing that is encouraged is, "Since Zen Cart version X, ..." (rather than "In Zen Cart version X and higher," for example). 

## Documentation Standards 

Please follow these rules when adding new documentation files to the `/content/user` and `/content/dev` folders: 

- Begin each file with front matter.  It's block that looks like:
<pre>
---
title: article title
description: article description 
category: article category
weight: 10
---
</pre>

- The title will be shown on the page, but the description will not; it is only shown as the subtitle for the page when the parent folder is being browsed. 

- The value of `weight` denotes a sort-order. Within folders, please set as follows: 

    - Use `weight: 10` as the default. This way alphabetic sorting will be used for most content, which is what is desired.

    - Use `weight: -1` for the first article in a folder (generally a "Using &lt;subsystem&gt;" or "About &lt;subsystem&gt;" type article). 
    
    - There are a few exceptions to this rule, such as Release History (sorted in reverse chronological order), Images (sorted by increasing complexity) and Admin Pages (sorted in the order they appear in Zen Admin), but for the most part, this rule is followed.

- If you want to use a title with a colon, put the entire title string in single quotes.  Example: 

```
title: 'Parse error:  unexpected T_STRING (or similar)'
```

- Don't use a headline starting with `#`.  The `title` in the block above is sufficient.

- Use backticks for denoting code and filenames.  For example, the filename "includes/classes/shopping\_cart.php" should be coded as 

```
`includes/classes/shopping_cart.php`
```  

This will make it appear as follows: `includes/classes/shopping_cart.php`.

- If you do need to escape an underscore outside of backticks, you can use a backslash, like this: `\_`.  

- If you are converting an old file from the Tutorials/FAQ area, be sure to change any references to `content.php` (the old way) to a new page on the docs site. Example: 

OLD WAY: 
```
Check out the <a href="https://www.zen-cart.com/content.php?48-what-are-the-server-requirements-to-run-zen-cart">Server Requirements For Running Zen Cart</a>;
```

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
Check out the [Server Requirements for Running Zen Cart](/user/first_steps/server_requirements.md).        **NO!**
</pre> 


- For consistency, use these standard names with no underscores:
    - `YOURSITE` - your domain name 
    - `YOURTEMPLATE` - your template name 
    - `YOURLANGUAGE` - your language (/english/ by default)
    - `YOURACCOUNTFOLDER` - your home folder provided by your hoster
    - `YOURSUBFOLDER` - if your site is below webroot   
    
    For details see the article [Basic Terms](user/new_user_topics/basic_terms). 

    **Please DO NOT use any other convention** like `/YOUR_CUSTOM_TEMPLATE/`, `/YOUR_STORE/`, `YOURSTORE`, `/your_site/`, `/custom/` , etc. - use the standard names above.  The reason underscores are not used in the documentation is that they are a special character for Markdown, so using them without backticks will mess up the formatting of a page. 

- Use a space padded greater than sign (` > `) for describing click paths in the Admin, rather than ellipses.  For example, use this: 

`Configuration > EZ-Pages Settings` 

NOT THIS:  

`Configuration ... EZ-Pages Settings`              **NO!** 

NOT THIS:  

`Configuration->EZ-Pages Settings`              **NO!** 

An exception is made for the frontmatter `title` where `>` is mangled by Algolia, so `≫` has been used instead. 

## Links 

- Use relative paths, starting with the folder under `/content`,  so people can test their changes locally.  Use this: 

`[Github Workflow](/dev/contributing/github_workflow/)`

NOT THIS:

`[Github Workflow](https://docs.zen-cart.com/dev/contributing/github_workflow/)`       **NO!** 

NOT THIS: 
`[Github Workflow](github_workflow/)`       **NO!** 

- Be sure to end an internal link with `/` unless it references an HTML anchor (has a "#" character).  Doing this consistently means checking for broken links is easier. 

`[Github Workflow](/dev/contributing/github_workflow/)`

NOT THIS: 
`[Github Workflow](/dev/contributing/github_workflow)`       **NO!** 

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

- For links to the Zen Cart download, please use the URL 

```
https://www.zen-cart.com/latest
```


<br />

## Renaming files

If it is necessary to rename or move a file, be sure to use [Hugo aliasing](https://gohugo.io/content-management/urls/) so as not break any external links to the page.  You can see an example of where this was done in the `/user/taxes/tax_calc_wrong.md` page, which used to be named `/user/locations/tax_calc_wrong.md`.  The front matter of the file has an alias to the old name: 

```
aliases:
    - /user/locations/tax_calc_wrong
```

Aliases can sometimes cause problems, so an alternate approach is to create a crosslink only page, as described below.

## Crosslink only pages 

A page with minimal content and mostly links is called a _crosslink only_ page. 
These pages are like linked products - they ensure that someone browsing a category will see related content.  An example is `/user/ezpages/ezpages_sidebox.md`.

The body of this page is just a link to the new page: 

```
Please see [this page](/user/sideboxes/ezpages_sidebox/).
```

Crosslink only pages should have `noindex: yes` in their front matter. 

We are no longer using a `url` in the front matter to redirect because it doesn't work reliably. 

## Excluding pages from the All FAQs index 

To avoid duplicate entries in the [All FAQs](https://docs.zen-cart.com/user/_allpages/) index, add the following line to the page frontmatter for pages with duplicate content: 

```
noindex: yes
```

## Excluding pages from a directory index

If you don't want a page to be shown when you click on a directory, add the following line to the page frontmatter: 

```
index: false
```

## Excluding pages from search results

To avoid duplicate entries in search results, add the following line to the page frontmatter for pages with duplicate content: 

```
nosearch: yes
```

## Markdown

* [Link to Markdown Syntax](https://www.markdownguide.org/basic-syntax/)

* For simplicity, use Markdown rather than HTML on these pages where ever possible. But remember that **when you embed markdown within an HTML block element, markdown formatting is disabled**.  To turn it back on, use a blank line before and after the markdown OR embed the content in a `<span>`.

* To embed an image, put the image in `/content/images` and use the `img` tag to display it: 

```
<img src="/images/version_link.png" alt="Zen Cart Version information" />
```

* Exercise caution when changing a header (a line preceded by one or more # signs).  The reason is that the text of this header is a link which is used to crosslink.  So if you have `### Header One`, then the link to this would be `[See Header One](/user/folder/file#header-one)`.  And if you change the "Header One" to something else, this link will no longer work! 


* Indenting in this system with bullet points requires four spaces. If you skimp and use 2, it may appear to work in your local markdown editor/viewer but it won't work when the site is deployed live!

<br />

## Advanced Effects 

More layout options are available than you might think - here are some examples:

- Accordion: [Release History](https://docs.zen-cart.com/user/about_us/release_history/) 

- Footnotes: [HTML Email Templates](https://docs.zen-cart.com/user/email/html_email_templates/) 

- Per page CSS: [What sideboxes are available?](https://docs.zen-cart.com/user/sideboxes/sidebox_list/)

- Popup Images: [What sideboxes are available?](https://docs.zen-cart.com/user/sideboxes/sidebox_list/)

- Tables: [How do I change the title of main\_page=page_X?](https://docs.zen-cart.com/user/new_user_topics/title_change_for_page_x/)

## Shared Content

Try not to copy and paste, since this means content will need to be maintained in multiple places. 

* If the shared content is structural, use a shortcode or modify a template.  This is an advanced area; please ask first.  
* Otherwise, simply link to the content in the main place it exists. See the section *Links* above. 
* Content created by shortcodes is stored in `layouts/shortcodes/`.  For example, the code fragment
```
{{% language_help_links %}}
```
pulls in `layouts/shortcodes/language_help_links.md`.

## Technical content 

- Please prefix the title of technical content with "Technical - ".
- Please include the shortcode `technical` at the top of the page. 

See `/user/upgrading/convert_to_utf8.md` for an example. 

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

## Reindexing of changes 

Documentation reindexing by Algolia occurs daily at 3am UTC.


