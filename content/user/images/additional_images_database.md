---
title: Additional Image Handling in the Database
description: Specifying additional image names in database fields 
category: images
weight: 10
---

In earlier versions of Zen Cart, additional images for a product were required to use the [filename matching mechanism](/user/images/image_filename_conventions/).

In Zen Cart 2.2.0, a new mechanism for specifying additional images was introduced.  The Configuration setting [Additional Images Handling](/user/admin_pages/configuration/configuration_images/#additional_images_handling) allows you to specify additional images in database fields, rather than relying on the older [filename matching mechanism](/user/images/image_filename_conventions/).

To specify additional images names in the database, follow these steps:

- Go to Admin > Configuration > Images and set Additional Images Handling to "Database."
- Go to Admin > Modules > Plugin Manager > Scan Additional Product Images to Database.  Install this plugin.
- Go to Tools > Scan Product Images To Database.

Once you run the scan tool, the new `products_additional_images` table will be populated, and you may use the product editing page directly to manage your additional images. 

![Additional Images on Product Edit page](/images/additional_images_product_edit.png)



