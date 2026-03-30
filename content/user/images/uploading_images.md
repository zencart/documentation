---
title: Uploading Images 
description: Methods for getting images to your site
category: images 
weight: 20
---

The majority of the images for your site will be product images, which will be handled either through the [product editing page](/user/products/product_edit/) or the [additional images feature](/user/images/additional_images_database/). 

But you may also have images on your home page or perhaps on other pages.  How can you get these images to your site so that you can reference their URLs when editing a page? 

Most developers will use an [FTP program](/user/first_steps/useful_tools/#ftp-tools) to transfer images from their computer to their host.  If you are not familiar with FTP, there is another easier method provided by cPanel's File Manager Tool.

Steps are as follows: 

1) Login to cPanel and open File Manager 

![File Manager](/images/fm1.png)

2) In File Manager, open the directory for your store.  This will correspond to the `DIR_FS_CATALOG` folder specified in your `includes/configure.php` file.  Typically it will start with `public_html`. 

3) You are now at the top level of your cart.  Open the folder `images/`.

4) On the left side of File Manager, press the "Upload" button.  This will open a new browser tab.  

![File Manager Upload button](/images/fm2.png)

5) Drag and drop your image or use the file selection dialog.  Select your image. 

![File Manager Upload page](/images/fm3.png)

Once the image has uploaded, press the "Go Back" link at the bottom of the screen.  You may upload more images if you need to. 
