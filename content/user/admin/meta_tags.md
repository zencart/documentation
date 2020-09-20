---
title: How do I set up meta tags for my site? 
description: 'Meta Tags: title, description and keywords'
category: admin
weight: 10
---

Zen Cart is built with a feature to have separate meta tags for each Category and Products -- separate from the ones on general pages.

### Categories
To define meta tags for a Category, go to the [Admin > Catalog > Categories/Products](/user/admin_pages/catalog/categories/).  Once you're there, click on the meta tag icon (the last one to the right for any given category) and set your content.

**Note:** A meta tag entry on this screen must contain something in the keywords and description fields or it is not considered complete, and will be ignored.

### Products
If you want to define meta tags for individual Products, you will navigate to that product using [Admin > Catalog > Categories/Products](/user/admin_pages/catalog/categories_products/), and click on the meta tag icon (last one on the right) to define it.

**Note:** there are custom settings in Product Types so if you don't want, for example, products_price in the title,  you can globally set the defaults for 1 or all product types.

### Common Site-Wide
To define site-wide tags such as charset, keywords and description, go to `/includes/languages/english/YOURTEMPLATE/meta_tags.php` and edit that file.  Set the keywords, site title, site tagline and site description.

### Custom Site-Wide
For meta tags not covered by the previous paragraph, edit 
`includes/templates/YOURTEMPLATE/common/html_header.php`. 
Open it up and add your own meta tag to those already there by default.


### PAGE-SPECIFIC Title, Description
For pages which only display "one thing", and are not dynamic lists or product/category/etc you can edit `/includes/languages/english/YOURTEMPLATE/meta_tags.php`, and create specific definitions for those items there.

Just follow the pattern as explained:

```
// Home Page Only:  define('HOME_PAGE_META_DESCRIPTION', '');
  define('HOME_PAGE_META_KEYWORDS', '');

// NOTE: If HOME_PAGE_TITLE is left blank (default) then TITLE and SITE_TAGLINE will be used instead.
  define('HOME_PAGE_TITLE', ''); // usually best left blank

// EZ-Pages meta-tags.  Follow this pattern for all ez-pages for which you desire custom metatags. Replace the # with ezpage id.
// If you wish to use defaults for any of the 3 items for a given page, simply do not define it.
// (ie: the Title tag is best not set, so that site-wide defaults can be used.)
// repeat pattern as necessary
  define('META_TAG_DESCRIPTION_EZPAGE_#','');
  define('META_TAG_KEYWORDS_EZPAGE_#','');
  define('META_TAG_TITLE_EZPAGE_#', '');

// Per-Page meta-tags. Follow this pattern for individual pages you wish to override. This is useful mainly for additional pages.
// replace "page_name" with the UPPERCASE name of your main_page= value, such as ABOUT_US or SHIPPINGINFO etc.
// repeat pattern as necessary
  define('META_TAG_DESCRIPTION_page_name','');
  define('META_TAG_KEYWORDS_page_name','');
  define('META_TAG_TITLE_page_name', ''); 

```
