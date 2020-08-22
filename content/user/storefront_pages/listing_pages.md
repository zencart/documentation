---
title: Listing Pages 
description: New Products, Featured Products, All Products and Product listing pages 
category: storefront_pages
weight: 10
---

Zen Cart uses the term _listing page_ to refer to a page that shows a number of products in a stack of rows in the center of the page. 

Examples of listing pages are: 

- All Products
- Featured Products
- New Products
- Product Listing pages 

The _Product Listing pages_ are the pages that are created when viewing a category which contains products (rather than other categories). 

_Category Listing pages_ are pages showing only categories.  This term is less used, and category listing pages have fewer configuration options.  Also, the category listing page is displayed as a grid of images, so it's different from the other listing pages discussed here. 

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

would be a category listing page, showing categories 5 and 6. 

The page showing category 5 (Shirts) 

```
index.php?main_page=index&cPath=3_5
```
would be a product listing page, showing products 4, 5 and 6. 

The listing pages described above are built in to Zen Cart; no extra work is required to create them.

Here's an example of what a product listing page might look like on a desktop computer: 

![Product Listing Page](/images/product_listing.png) 

The layout and configuration for listing pages is described in [listing page layout](/user/template/listing_page_layout/). 

