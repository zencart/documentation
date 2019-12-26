---
title: Turning off Additional Images
category: Zen Cart
weight: 2
---

# Turning off Additional Images
 
## Problem:

On my product pages, I'm seeing images from other products showing under my product description.  Why? How do I change this?

## Cause:

The "additional images" feature is causing this.

## Solution:

You have two options:

a) rename your images so they don't share a common filename.  Right now since you have one product with "abc.jpg" as the name, and another product with "abcde.jpg" as the name, both images will show for the "abc.jpg" product, because "abc" is common to both, and "abc" is the full filename of the main image of one of the products.  
This is explained further in the [Additional Images Tutorial](customizing/adding_multiple_images_to_a_product.md).

b) or turn off all extra-image functionality via Admin->Catalog->Product Types->Product General->Edit Layout->Show Additional Images = 0
