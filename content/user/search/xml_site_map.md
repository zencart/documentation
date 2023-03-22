---
title: XML Site Map Page
description: A sitemap for search engines 
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

**NOTE:** You should not use random utilities found from a web search to create an XML site map; use a Zen Cart aware program like the plugin noted above instead.  The reason is that a naive sitemap builder will include the `cPath` parameter in the `product_info` page URL, whereas the canonical URL will not, which will cause search engines not to not index these pages. 

Example: 

```
<url>
  <loc>https://YOURSITE.net/index.php?main_page=product_info&cPath=19&products_id=66</loc>
  <lastmod>2022-07-18T22:38:55+00:00</lastmod>
  <priority>0.80</priority>
</url
```

Submitting a non-canonical URL like this will yield the following from Google: 

![URL inspection error](/images/URL_inspection.png)

When you switch to a sitemap that uses canonical URLs, the page will be indexed. 
