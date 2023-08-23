---
title: Image Preparation - how to 
description: Preparing and Optimizing Images for Zen Cart 
category: images
weight: 10
---

If you are uploading photographic-type images, the format should be `.jpg`; if you are using clip-art style pictures, the images should be in `.gif` or `.png` format.  

- You cannot have a transparent background with a `.jpg` but you can with a `.gif` or `.png`.  
- Never save a photograph as a `.gif` - not only do you lose a lot of quality, but due to the way data is stored as a `.gif`, the file size will be far larger than it ought to be! Use `.jpg` for photographs.
- The file size of an image is entirely dependent on three factors: the physical dimensions, the format it is saved in, and the amount of compression applied. You may have heard things about image resolution - that has nothing to do with the file size.  
- These file types use what is called “lossy” compression i.e. when the file is compressed, some information is discarded.  
Once the file is saved in a lossy format, the lost information cannot be recovered! Therefore, always start with a copy of the best image you have and never compress the original.

File size is still an important issue: It's always best to use smaller sizes whenever possible because mobile devices use slower download speeds unless they're on a fast Wi-Fi connection. Always plan your website assets for the slowest connection your customers will usually use.

**Images for the Internet**

While we all want the best graphics for our websites, we need to make sure we don't make it difficult for our customers' browsers to process our files.  Not all of these suggestions are written in stone, but following these guidelines at the beginning of image preparation will help you immensely.  The most important is image naming.

Three suggestions when naming an image are:

- Do not use spaces in a filename.  It's tempting to create `image of main product.jpg` but the spaces can often be misinterpreted. (Even adding `%20` as sometimes is done can be problematic. Better not to do that.) Use something like `mainProductImage.jpg`. That way the filename is still able to be read and understood that this is the image for the main product.  Spaces can be used in alt text and image titles (which Zen Cart provides from the product/category name).
  - If you want to know the number of images in your database that contain a space, you can run the following code as a query to your database:  `SELECT COUNT(products_id) AS num_products_with_space_in_image
FROM products
WHERE products_status = 1 AND products_image LIKE '% %';`
  - If you want a listing of the images with a space and the Product ID of that image, you can run the following code as a query to your database:  `SELECT products_id, products_image
FROM products
WHERE products_status = 1 AND products_image LIKE '% %';`
- Don't use capitals to start an image filename or for the file extension.  `MainProductImage.jpg`, `MainProductImage.JPG`, `mainProductImage.jpg` and `mainProductImge.JPG` are not the same on the web.  They would be considered as four different files.  Capitals "can" help make sense of an image name but, save the use of beginning capital letters for the alt text and image title.
  - If you want to know the number of images in your database that begin with a capital letter, you can run the following code as a query to your database:  `SELECT COUNT(products_image) AS num_products_images_starting_with_capital
FROM products
WHERE BINARY LEFT(products_image, 1) = UPPER(LEFT(products_image, 1));`
  - If you want a listing of the images in your database that begin with a capital letter and the Product ID of that image, you can run the following code as a query to your database:  `SELECT products_id, products_image
FROM products
WHERE BINARY LEFT(products_image, 1) = UPPER(LEFT(products_image, 1));`
  - If you want to know the number of images in your database that have the file extension in capital letters, you can run the following code as a query to your database:  `SELECT COUNT(products_id) AS num_products_with_capitalized_extension
FROM products
WHERE BINARY SUBSTRING_INDEX(products_image, '.', -1) = UPPER(SUBSTRING_INDEX(products_image, '.', -1));`
  - If you want a listing of the images in your database that have the file extension in capital letters and the Product ID of that image, you can run the following code as a query to your database:  `SELECT products_id, products_image
FROM products
WHERE BINARY SUBSTRING_INDEX(products_image, '.', -1) = UPPER(SUBSTRING_INDEX(products_image, '.', -1));`
- Try to be as descriptive as possible in your image name.  The previous `mainProductImage.jpg` mentioned above may make perfect sense to you but not to anyone else who doesn't know what your main product is.  If your main product is a children's dresser made from natural pine and has four drawers, it can be presented in several ways. Consider how customers find your site when naming a file: If they are looking for children's items, perhaps `childrens-dresser-4drawer-pine.jpg` would work.  If folks come to your site looking for a particular wood, then `pine-4drawer-childrens-dresser.jpg` might be better for your site.

These are recommendations to help create a standard naming practice before adding images to your site.  We hope they make dealing with images much easier.

**Zen Cart and image handling**  

Zen Cart displays images in 3 sizes - the small ones (thumbnails) shown in the various listings, a medium size used just on the Product Info page, and a large version accessed from the "larger image" link on the Product Info page.

You can set the display size for the small and medium images by going to [Admin > Configuration > Images](/user/admin_pages/configuration/configuration_images/). If you want all your images to be the same width but the heights may vary, then set the Width to the fixed maximum you require and the height to 0 and make sure *Calculate Image Size* is turned on. Conversely, if you want all the images to be the same height, then set the Width to 0 and the height to the maximum you require.  

After this you could simply upload all your pictures using your [FTP tool](/user/first_steps/useful_tools/#ftp-tools) to your `/images` folder and let the coding do all the work - but this will generally end up with you having a far from perfect result. 

Why are the results not (usually) perfect? The ideal we are seeking is a clear image that displays quickly, but by only loading one image to be used in a variety of sizes by ZC, there is usually going to be a compromise on one or the other - or both. 

For example, if you only provide the images at the small 100 pixels width and you have your medium image width set to 400 for the Product Info page, then the quality of your medium-size image is going to be degraded (remember the “lossy” compression?) when the code expands it to four times the size.

On the other hand, if you’ve uploaded image files at say 400 pixels wide, then although Zen Cart will display them correctly for both small 100px and medium 400px sizes in the right places, those 400px images might be 25KB (larger than needed for displaying at 100px size) ... so if you have 10 100px thumbnails on a page at 25KB each that makes 250KB which starts to slow your listings down to a crawl for mobile visitors.

To avoid these issues, the solution is to create 3 sets of images – small, medium, and large, compressed and saved at the dimensions you wish to display them and then uploaded to the **images**, **images/medium**, and **images/large** directories. If you have hundreds of images, this may seem like a daunting prospect, but it shouldn’t be quite as bad as it sounds. Any decent image-editing application will have some system for batch processing (carrying out the same actions on multiple files).  

**NOTE:** The basic "images" (thumbnails, normal-size images) should be uploaded via your admin in the usual way via the product-edit screen, and then FTP should be used for uploading your `_MED` and `_LRG` images, as mentioned in the following section.  

**Optimising images for Zen Cart**  

Start by deciding on the size at which you want the large image to be displayed.  

You can’t set the dimensions of the large image (shown when the visitor clicks the Larger Image link) in Zen Cart, but it will display at the dimensions you upload it.

You shouldn’t choose a size larger than that of the original (if you have to expand it, you will likely lose quality). For most purposes, making the large image 480 or perhaps 640 pixels wide should be sufficient.  


Scenario:
Let’s assume you are working with a collection of photographs taken with a digital camera, with a mix of landscape and portrait images. This in itself poses another “problem” in that the layout of your pages will vary slightly depending on whether your image is sideways or upright. For the sake of uniformity throughout your site, it would be good to decide on a square image size and re-size your photographs to fit horizontally or vertically as required and the remaining area is just “white space” (unless you have a different color as your background, in which case you could choose that color or transparent if you're saving as `.png`.)

In this example scenario we want the large picture to be either 480 pixels wide or 480 pixels high depending on its orientation so that everything remains in proportion; we want the medium picture to be 240 and the small to be 120. Let's assume that all your images will have unique names (see the naming suggestions above). Having said that, Zen Cart requires that the image filenames follow a pattern, where the base/thumbnail images are called `imagename.jpg` and large images are called `imagename_LRG.jpg` and medium are called `imagename_MED.jpg` – [graphics editors](/user/first_steps/useful_tools/#graphics-editors) allow renaming of multiple files. They also allow some of the processing below. 

1. Gather all the images in a folder on your hard drive.  
2. Copy all the landscape orientated pics to a new folder (call it **landscape**)  
3. Copy all the portrait-orientated pics to another new folder (**portrait**)  
4. Run your image editor's batch processor (<font color="red">you’ll have to find out how to do this from your image-editor manual/help files</font>) on the files in the **landscape** folder to re-size them all to the same width (use 480px – and if you are using standard digital photos, this should give you a height of 360)  
5. Repeat the above on the files in the **portrait** folder to re-size them all to the same height (i.e. 480px – should give you a width of 360)  
6. Now run another batch process on the two folders to  
• Resize your canvas or paper (depending on what your image editor calls it) to 500 pixels x 500 pixels and set the canvas or paper color you want with the image centered. (Using a canvas slightly larger than your picture ensures a margin from anything else that may be on the webpage.)  
• Optimize the images for the web  
7. Unless you want to keep them separate you can now combine all the images into one folder called **large** as they are all 500 pixels square.  
8. Upload them all to **images/large**  
9. Create another folder called **medium**. Copy all the images from **large** to it. 
10. Run a batch process on the files in **medium** to resize to 250 pixels square; you may as well optimize for the web as well.  
11. Upload them all to **images/medium**  
12. Create another folder called **small**. Copy all the images from **large** to it.  
13. Run a batch process on the files in **small** to resize to 125 pixels square; you may as well optimize for the web as well.  
14. Upload the resized **images/small** files to the **images** folder (yes, "images", not "images/small") on the server.

You have now given Zen Cart the best chance of giving your visitors the best visual display at the optimum download time.
