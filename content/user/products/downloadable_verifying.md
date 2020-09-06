---
title: Downloadable products - verifying correctness 
description: Check your downloads after creating them
category: products
weight: 10
---

Once you have created downloadable products, or after you have updated them, you'll want to check on them to be sure they will work for your customers.  There are a couple of ways to do this. It is also particularly important to do this if you [move the download folder](/user/security/relocate_download_folder/) for security reasons. 

### Downloads Manager 
Going to [Admin > Catalog > Downloads Manager](/user/admin_pages/catalog/downloads_manager/) shows a screen with two downloadable products.  Note that the first download (named test.zip) is missing, which is shown by the red dot next to the filename. 

<br>
<img src="/images/downloads_manager.png" alt="Downloads Manager" />

### Attributes Controller 

Going to [Admin > Catalog > Attributes Controller](/user/admin_pages/catalog/attributes_controller/) and viewing a single product which has downloads allows you to see if the downloadable files are present where they should be. 
In the image below, you can see again that the file test.zip is missing.

<br>
<img src="/images/attributes_controller_attributes.png" alt="Attributes Controller" />

### Product Edit page 

Editing a product shows you the shipping settings, which are required to be as follows for a downloadable product: 

- Product is Virtual: No, Shipping Address Required
- Always Free Shipping: No, Normal Shipping Rules

See [shipping costs](/user/products/downloadable/#additional-notes-about-downloads-and-shipping-costs) for more details. 


