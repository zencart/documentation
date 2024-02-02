---
title: Working with Additional Images 
description: Having multiple images for a product
category: images 
weight: 20
---

### How do I enable the additional images feature? 
Go to [Admin > Catalog > Product Types](/user/admin_pages/catalog/product_types/),
then selecting `Product - General` (or whatever your product type is),
then clicking *Layout Settings*, and setting `Show Product Additional Images` to 1.

Then add additional images for your products, following the naming 
conventions set out in [Image Filename conventions](/user/images/image_filename_conventions/). 


### How do I disable the additional images feature? 

Go to [Admin > Catalog > Product Types](/user/admin_pages/catalog/product_types/),
then selecting `Product - General` (or whatever your product type is),
then clicking *Layout Settings* and setting `Show Product Additional Images` to 0.

### Why do I see images for other products on my product pages?

The additional images feature is causing this because of misconfigured image filenames. 

You have two options:  

a) rename your images so they don't share a common filename.  Right now since you have one product with "abc.jpg" as the name, and another product with "abcde.jpg" as the name, both images will show for the "abc.jpg" product, because "abc" is common to both, and "abc" is the full filename of the main image of one of the products.   

This is explained further in [Image Filename Conventions](/user/images/image_filename_conventions/). 

b) or turn off all extra-image functionality by following 
the directions above to disable additional images.

### Is there an easier way to manage multiple product images? 

The popular plugin [Image Handler](/user/images/image_plugins/) allows you to manage multiple product images. 

### How will additional images appear? 

Additional images are shown below the main product image, and can be clicked on the same way the main image can - see [Popups](/user/images/popups).

This product has one additional image.

![Single Additional Image](/images/main_additional_1.png)

This product has multiple additional images. 

![Multiple Additional Images](/images/main_additional_2.png)

