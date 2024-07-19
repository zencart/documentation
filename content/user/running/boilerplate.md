---
title: Boilerplate 
description: Using repeating blocks of text in your Zen Cart
category: running 
weight: 10
---

"Boilerplate" is a term that means "standardized blocks of text." 

There's no need to re-type the same text in multiple places. 
Try these plugins to save time and make your life easier! 

## Order Comments Boilerplate 

This plugin allows you to reuse blocks of text to paste into the order comments field on the Order Details page. 

[Order Comments Boilerplate](https://www.zen-cart.com/downloads.php?do=file&id=2222)


## ShortCodes for Zen Cart 

Styled after WordPress shortcodes, this plugin makes it easy for you to inject links to categories and products. 

[ShortCodes for Zen Cart](https://www.zen-cart.com/downloads.php?do=file&id=2394)

## Define Page Anywhere 

This plugin allows you to pull in define page content (which can be easily edited in your Admin) into any page in your cart, including the product info page under conditions you specify. 

[Define Page Anywhere](https://www.zen-cart.com/downloads.php?do=file&id=2333)

## Boilerplate Text on your Product Descriptions 

This set of instructions allows you to define a block of text once and use it repeatedly in product descriptions.

a) Create boilerplate defines

You will be defining your boilerplate strings in a file called `includes/languages/english/extra_definitions/my_defines.php` Each string will have a PHP "define" statement, and all the strings will be listed in an array. In this way, users can simply add and delete strings by editing this one file, rather than having to dig into the internals of Zen Cart.

We'll use a simple example:
```
<?php

$descr_stringlist = array("PHP_ONE_WEEK_DELAY", "PHP_TWO_WEEK_DELAY", "PHP_THREE_WEEK_DELAY"); 
$GLOBALS['descr_stringlist'] = $descr_stringlist; // required for Zen Cart 1.5.8 only 

define('PHP_ONE_WEEK_DELAY', 'These decals will be shipped in one week after receiving your order.'); 
define('PHP_TWO_WEEK_DELAY', 'These decals will be shipped in two weeks after receiving your order.'); 
define('PHP_THREE_WEEK_DELAY', 'These decals will be shipped in three weeks after receiving your order.'); 
```

We've defined three constants and added each one to a list called `$descr_stringlist`.

b) Update your product info template

Edit the file 
`includes/templates/YOURTEMPLATE/templates/tpl_product_info_display.php`

Change
```
 <!--bof Product description -->
<?php if ($products_description != '') { ?>
<div id="productDescription" class="productGeneral biggerText"><?php echo stripslashes($products_description); ?></div>
<?php } ?>
<!--eof Product description -->
```

to
```
 <!--bof Product description -->
<?php if ($products_description != '') { ?>
<div id="productDescription" class="productGeneral biggerText">
<?php 
$stripped_products_description = $products_description;
foreach ($descr_stringlist as $varname) { 
   $stripped_products_description = str_replace($varname, constant($varname), $stripped_products_description);
}
?>
<?php echo stripslashes($stripped_products_description); ?></div>
<?php } ?>
<!--eof Product description -->
```

Now to use this logic, all you need to do is type `PHP_ONE_WEEK_DELAY` in your product description (under Admin - Catalog - Categories and Products), and when you display the product info page, it will be changed.

If you display the Description in any of the other lists (Product Listing, New Listing, Featured Listing, All Listing), you will need to modify code that handles the product description for listing pages (in `includes/modules/YOURTEMPLATE/product_listing.php`) in the same way. Alternately, you can just set "Display Product Description" to 0 on those screens (available under Admin - Configuration).

If you just want to add some boilerplate text based on category, product name, or some other field, you can do that too, without having to type it in to each product in the Admin interface. For instance, here's some logic that adds the string `CAT1_DESC` - which you have defined in the file `includes/languages/english/extra_definitions/my_defines.php` - to every product in category 1:

```
<!--bof Product description -->
<?php if (($products_description != '') || ($current_category_id == 1) ) { ?>
<div id="productDescription" class="productGeneral biggerText">
<?php 
   $stripped_products_description = $products_description;
   if ($current_category_id == 1)  {
      $stripped_products_description = $stripped_products_description . CAT1_DESC;
   }
   echo stripslashes($stripped_products_description); 
   echo '</div>';
?>
<?php } ?> 
<!--eof Product description -->
```

Adding boilerplate to every product whose name includes some specific string is similar, but instead of using a simple numeric equality check, a regular expression must be used. This code fragment will add `FISH_STR` to the product description of every product whose product name ends with the string " fish."
```
<!--bof Product description -->
<?php 
if (preg_match("/.* fish$/", $products_name)) {
   $products_description = $products_description . FISH_STR;
}
if (($products_description != '') { 
   echo '<div id="productDescription" class="productGeneral biggerText">';
   echo stripslashes($products_description); 
   echo '</div>';
}
?>
<!--eof Product description -->
```

What if you really want to add links and not static strings? Well, this is done in a very similar way. Instead of using the static strings described above, in the file `includes/languages/english/extra_definitions/my_defines.php`, add the code

```
<?php

$descr_stringlist = array("RED_LINK", "BLUE_LINK"); 
$GLOBALS['descr_stringlist'] = $descr_stringlist; // required for Zen Cart 1.5.8 only 
define('RED_LINK', '<a href="' . zen_href_link(FILENAME_DEFAULT, 'cPath=2') . '">' . 'red cars' . '</a>'); 
define('BLUE_LINK','<a href="' . zen_href_link(FILENAME_ADVANCED_SEARCH_RESULT, 'keyword=search+string') 
    . '">' . 'something else' . '</a>'); 
```

... and instead of using the PHP_*_WEEK_DELAY strings above, you would use one of these strings in your description.


