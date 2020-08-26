---
title: Listing Pages 
description: New Products, Featured Products, All Products and Product listing pages 
category: storefront_pages
weight: 10
---

Zen Cart uses the term _listing page_ to refer to a page that shows a number of products in a stack of rows in the center of the page. 

Examples of listing pages are: 

Page | URL 
-----|-----
All Products | index.php?main_page=products_all
Featured Products| index.php?main_page=featured
New Products | index.php?main_page=products_new 
Product Listing | index.php?main_page=index&cPath=NNN

Where _NNN_ is a category path of a category containing products. 

The _Product Listing pages_ are the pages that are created when viewing a category which contains products (rather than other categories). 

_Category pages_ are pages showing only categories.  This term is less used, and category pages have fewer configuration options.  Also, the category page is displayed as a grid of images, so it's different from the other listing pages discussed here. 

Consider the following product hierarchy 

<pre>
Men's Clothing (category 3)
     |
     ---->  Shirts (category 5)
     |      |
     |      -------> shirt A  product 1
     |               shirt B product 2
     |               shirt C  product 3
     ---->  Pants (category 6)
     |      |
     |      -------> pants A  product 4
     |               pants B product 5
     |               pants C  product 6 
</pre>

The page showing category 3 (Men's Clothing) 

```
index.php?main_page=index&cPath=3
```

would be a category page, showing categories 5 and 6.  The category path for this page would be _3_. 

The page showing category 5 (Shirts) 

```
index.php?main_page=index&cPath=3_5
```
would be a product listing page, showing products 4, 5 and 6.  The category path for this page would be _3_5_. 

In the cases above, the category pat hfor the 

The listing pages described above are built in to Zen Cart; no extra work is required to create them.

Here's an example of what a product listing page might look like on a desktop computer: 

![Product Listing Page](/images/product_listing.png) 

And here's the Featured Products listing page showing a different layout: 

![Featured Products Listing Page](/images/product_listing_featured.png) 

The layout and configuration for listing pages is described in [listing page layout](/user/template/listing_page_layout/). 

