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

### Additional images filename matching rules

In Zen Cart 2.2.0, a new mechanism for specifying additional images was introduced; please see [Additional Images Handling in the Database](/user/images/additional_images_database/) for details.

Using an underscore and more characters after the base filename is the best practice for ensuring your additional images work as expected.  See [Image Filename Conventions](/user/images/image_filename_conventions/) for details. 

Prior to Zen Cart 2.1.0, image matching did not enforce the check of a `_` suffix when looking for additional product images in the "images/" directory (but it DID require the `_` in any `images/whatever/` subdirectories). Starting with Zen Cart v2.1.0 a stricter matching pattern requires the `_` in both locations, by default, but can be overridden. 

Stores that are upgrading from pre-2.1.0 will automatically retain the old functionality by default, but can switch over to strict mode by changing the [Admin > Images >Additional Image matching pattern](/user/admin_pages/configuration/configuration_images/) setting from `legacy` to `strict`.

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

To add images to a product using Image Handler, 

- Go to Tools > Image Handler
- On the Image Manger tab, drill down to the category and then the product 
- Click the button "Click to add a new image to this product."

Note that the product must be enabled for you to do this. 

### How will additional images appear? 

Additional images are shown below the main product image, and can be clicked on the same way the main image can - see [Popups](/user/images/popups).

This product has one additional image.

![Single Additional Image](/images/main_additional_1.png)

This product has multiple additional images. 

![Multiple Additional Images](/images/main_additional_2.png)

