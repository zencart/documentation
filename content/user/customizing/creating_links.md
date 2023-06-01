---
title: Creating Links to Other Pages 
description: How to create intra-site links 
category: customizing 
weight: 10
---

# Linking from HTML 

Sometimes, like when you're [adding a link to the Information Sidebox](/user/sideboxes/add_link_information_sidebox/), you have the ability to use PHP in building both the link and the anchor text.  

But sometimes you won't be able to use PHP.  Examples of this situation are:

- Modifying a category description to add a link 
- Modifying a product description to add a link 
- Modifying an EZ Page to add a link 

No worries, even though you can't use PHP, you can still create a link to another page using straight HTML.

Note that all link hrefs should start with `index.php` *not* `/index.php`.  This will allow you to move the site to a subfolder, for example during testing. 

If you are doing this in CKEditor, be sure to press the **Source** button so that you may enter straight HTML source code.  If you are using Plain Text, you can just enter the HTML code in.  

## Linking to a Product from HTML
To link to product 6, the Widget product, you would use 

```
<a href="index.php?main_page=product_info&products_id=6">Widget</a>
```

Note that this will work for products whose `product_type` is set to 1. 
If this is not the case, use 
the specific `main_page` setting for their  product type.  For example, 
```
index.php?main_page=product_music_info&products_id=166
```

## Linking to a Category from HTML
To link to category 9, the Anvils category, you would use 

```
<a href="index.php?main_page=index&cPath=9">Anvils</a>
```

## Linking to an EZ Page from HTML 
To link to EZ Page 8, titled "FAQ", you would use 

```
<a href="index.php?main_page=page&id=8">FAQ</a>
```

## Linking to another built-in page from HTML 
Go to the page and note the URL.  Then trim off everything before `index.php` and use the remainder. 

For example, your contact us page might be 

```
https://acme.com/store/index.php?main_page=contact_us
```

Trim off everything before the `index.php` and use that. 

```
For more help, please <a href="index.php?main_page=contact_us">Contact Us</a>.
```

# Linking from PHP

If you're linking from PHP, you are likely editing a code file.  Here are some ideas on what to add to build your link.

## Linking to a Product from PHP 
To link to product 6, the Widget product, you would use 

```
<a href="index.php?main_page=product_info&products_id=6">Widget</a>
```

Note that this will work for products whose `product_type` is set to 1. 
If this is not the case, use 
the specific `main_page` setting for their  product type.  For example, 
```
index.php?main_page=product_music_info&products_id=166
```

## Linking to a Category from PHP 
To link to category 9, the Anvils category, you would use 

```
$cat_id = 9; 
<a href="<?php echo zen_href_link(FILENAME_DEFAULT, "cPath=".$cat_id);?>"><?php echo zen_get_category_name($cat_id);?></a>
```

or 

```
$cat_id = 9; 
echo '<a href="' . zen_href_link(FILENAME_DEFAULT, "cPath=".$cat_id) . '">' . zen_get_category_name($cat_id) .'</a>'; 
```

## Linking to an EZ Page from PHP 

To link to EZ Page 19, 
``` 
$pages_id = 19; 
echo '<a href="' . zen_ez_pages_link($pages_id) . '"></a>';
```

