---
title: CSS 
description: Stylesheet customization in Zen Cart 
category: template
weight: 10
---

In Zen Cart, stylesheets are located in this folder: 
`/includes/templates/YOURTEMPLATE/css`. 

The CSS files are sent to the browser in this order: (and alphabetically within each case of more than one match):

1. `style*.css` // are always loaded and at least ONE should contain site-wide properties. 

1. `language_stylesheet.css` // changes to ALL pages, when that language is used

1. `page_name.css` // changes to one page (use index_home.css for "just the home page") 

1. `pageXXX.css` // changes for a specific numbered EZ-Page, ie: page3.css for ez-page id=3 

1. `language_page_name.css` // changes to one page, when that language is used

1. `c_??.css` // changes to all info pages in a category

1. `language_c_??.css` // changes to all info pages in a category, when that language is used

1. `c_??_??_children.css` // changes for all children of the specified parent. Also supports a language prefix. 

1. `m_??.css` // changes to a manufacturer's listing page

1. `language_m_??.css` // changes to a manufacturer's listing page, when that language is used

1. `p_??.css` // changes to a product's info page

1. `language_p_??.css` // changes to a product's info page, when that language is used

1. `print*.css` // printer-friendly global usage site-wide changes for printing-only 

The `stylesheet.css` always loads first and should contain the bulk of your CSS selectors. Each file loaded takes priority over previously loaded file(s). To save loading time, only new selectors or selectors whose properties you wish to change should be in the subsequent optional CSS files. You can have different overrides for the same page, in different languages, because the two would never be called at the same time.

`If someone selected the French language on your site, the `french_stylesheet.css` would also be loaded. It should only contain the site-wide changes you want to make to `stylesheet.css`. 

If someone went to any of the other pages, that page's CSS file would be loaded. Possibly you want different `background-image` & `background-color` on each of `page_x` pages. Possibly you do not want a border around `.plainBox` most of the time, but on a couple of pages you do, and on one of those pages you want it in black and the other in red.

Possibly you created a NEW tag for your Privacy Statement. It is defined in only one CSS file, `german_privacy.css` as 

```
.newtag { text-transform: uppercase }
```

Because, in Germany, that phrase must be in all CAPS, but not in other countries.

Use your CSS files and the standard tags as much as possible; just change their properties when needed. If possible, DON'T MODIFY the core code. Use your CSS files to do the work for you.

If you refrain from altering the core files, then you will find that upgrades and maintenance are much easier.

Helpful tips testing CSS changes: 
- Watch out for [browser caching](/user/new_user_topics/browser_caching/).
- Use [Inspect in Google Chrome](/user/running/inspect/).

