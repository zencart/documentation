---
title: Site Map Page
description: The store site map 
category: storefront_pages
weight: 10
---

Since Zen Cart 1.3.0, a storefront sitemap has been automatically produced.  The purpose of this sitemap is to provide visitors with a single place to see all the categories in the store.  It's just another mechanism for your customers to discover what's in your store. 

Other pages are also included in the Site Map, such the [Define Pages](/user/template/define_pages/), [Advanced Search Page](/user/search/storefront_search/#advanced-search-page) and [EZ-Pages](/user/ezpages/).

![Site Map](/images/sitemap.png)

This site map is produced for the benefit of human visitors, and should not be confused with an [XML sitemap](/user/search/xml_site_map/), which is produced for the benefit of search engines. 

The site map may be accessed at the URL `index.php?main_page=site_map`.  There is frequently a link to the site map in a store's footer, header or a sidebox. 

## Extending the Site Map 

You may wish to extend your sitemap if you have customized your site in the following ways: 

- [Custom added pages](/user/customizing/add_pages/)
- [Non-product Downloads](/user/products/downloads_not_products/)

The easiest way to do this is to 

- Copy the file `includes/templates/template_default/templates/tpl_site_map_default.php` to your template (i.e. `includes/templates/YOURTEMPLATE/templates/tpl_site_map_default.php`) 
- Either add specific references to files (the way `FILENAME_SPECIALS` is handled) or add PHP code that creates a list dynamically (either using a database query or a filesystem operation). 

If you want to list all the files in the folder, these StackOverflow posts might help: 

- [Display all files in a directory sorted alphabetically](https://stackoverflow.com/questions/3977500/how-can-i-list-all-files-in-a-directory-sorted-alphabetically-using-php?rq=3)
- [Display all PDF files in descending order of upload date](https://stackoverflow.com/questions/40861946/how-can-i-display-and-list-all-pdf-files-in-a-directory-in-an-html-table-in-the) 

