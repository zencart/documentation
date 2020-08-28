---
title: XML Site Map Page
description: An sitemap for search engines 
category: search 
weight: 10
---

Search engines like Google prefer to consume site maps in XML, which is more efficient than a site map created in HTML, with markup to make it attractive to humans.  Sitemaps produced for search engines are designed using the format defined by [sitemaps.org](https://www.sitemaps.org/index.html).

A plugin is available to produce an [XML sitemap for your store](https://www.zen-cart.com/downloads.php?do=file&id=367).  After installing and running this plugin, you can submit the resultant files to Google for indexing. 


The XML sitemap is a series of text files that follow a specific format.  Here's what one entry from the product sitemap might look like:

```
 <url>
  <loc>http://YOURSTORE.com/shop/index.php?main_page=product_info&amp;products_id=181</loc>
  <lastmod>2020-08-21</lastmod>
  <changefreq>weekly</changefreq>
  <priority>1.00</priority>
 </url>
```

This site map is produced for the benefit of search engines, and should not be confused with the [storefront sitemap](/user/storefront_pages/site_map/), which is produced for the benefit of human visitors. 

