---
title: Image Preparation - how to 
description: Preparing and Optimizing Images for Zen Cart 
category: images
weight: 10
---

If you are uploading photographic type images, the format should be .jpg; if you are using clip-art style pictures, the images should be in .gif or .png format.  

• You cannot have a transparent background with a .jpg but you can with a .gif/.png.  
• Never save a photograph as a .gif - not only do you lose a lot of quality, but due to the way data is stored as a .gif, the file size will be far larger than it ought to be!  
• The file size of an image is entirely dependant on the physical dimensions, the type of format it is saved in and the amount of compression applied. You may have heard things about image resolution - that has nothing to do with the file size (but a heck of a lot to do with the quality of a printout! That's another topic altogether!).  
• These file types use what is called “lossy” compression i.e. when the file is compressed, some information is discarded.  
Once the file is saved in a lossy format, the lost information cannot be recovered! Therefore, always start with a copy of the best image you have and never compress the original.  

File size is still an important issue - even with the spread of broadband, the majority of people connecting to the web are still on dial-up connections, and unless you are aiming at a specifically broadband market, then you should endeavour to keep file sizes to a minimum commensurate with quality to enhance your viewers’ experience. 

**Images for the Internet**

While we all want the best graphics for our websites, we need to make sure we don't make it difficult for the Internet or browsers to process our files.  Not all of these suggestions are written in stone but, following these guidelines in the beginning of image preparation will help you immensely.  The most important is image naming.

There are three things we recommend when naming an image are:
• Do not use spaces in a filename.  It's tempting to create 'image of main product.jpg' but, the spaces often create problems for browsers as they do not all process the space in the same manner.  Just the addition of the '%20' (often substituted for the space) can often be a problem.  Instead, if you are not going to use a more descriptive name, use something like 'mainProductImage.jpg'.  The filename is still able to be read and understood that this is the image for the main product.  Spaces can be used in alt text and image titles.
• Don't use capitals to start an image filename or for the file's extension.  MainProductImage.jpg, MainProductImage.JPG, mainProductImage.jpg and mainProductImge.JPG are not the same on the web.  They would be considered as four different files.  Capitals "can" help make sense of an image name but, save the use of beginning capital letters for the alt text and image title.
• Try to be as descriptive as possible in your image name.  The previous mainProductImage.jpg may make perfect sense to you but not to anyone else who doesn't know what your main product is.  If your main product is a children's dresser that's natural pine and has four drawers, it can be presented in several ways.  Consider how customers find your site when naming a file.  If they are looking for children's items, perhaps 'childrens-dresser-4drawer-pine.jpg' would work.  If folks come to your site looking for a particular wood, then 'pine-4drawer-childrens-dresser.jpg' might be better for your site.

These are recommendations to help create a standard naming practice before adding images to your site.  We hope they make dealing with images much easier.

**ZC and image handling**  

ZC displays images in 3 sizes - the small ones (thumbnails) shown in the various listings, a medium size used on the Product Info page and a large version accessed from the "larger image" link on the Product Info page.
You can set different sizes for the different types of listing, but I'd suggest for the sake of uniformity through your site that you set all those to the same dimensions as your "small" setting.

You can set the sizes for the small and medium by going to [Admin > Configuration > Images](/user/admin_pages/configuration/configuration_images/). If you want all your images to be the same width but the heights may vary, then set the Width to the figure you require and the height to 0 and make sure *Calculate Image Size* is turned on. Conversely, if you want all the images to be the same height, then set the Width to 0 and the height to the figure you require.  

You can now simply upload all your pics using your [FTP tool](/user/first_steps/useful_tools/#ftp-tools) to your `/images` folder and let the coding do all the work - but this will generally end up with you having a far from perfect result. 

Why are the results not (usually) perfect? The ideal we are seeking is a clear image that displays quickly, but by only loading one image to be used in a variety of sizes by ZC, there is usually going to be a compromise on one or the other - or both. 

For example, if you only load small images at 100 pixels wide and you have your medium image width set to 400 for the Product Info page, then the quality of your image is going to be degraded (remember the “lossy” compression?) when the code expands it to four times the size.  

On the other hand, if you’ve only uploaded large files at say 400pixels wide, then although ZC will display them at your small image size of 100pixels wide, the file size of the image will not be reduced, so if your large image is 25KB, then so will your thumbnail be…and 10 thumbnails on a page makes 250KB which starts to slow your listings down to a crawl for dial-up users.  

To avoid these issues, the solution is to create 3 sets of images – small, medium and large, compressed and saved at the dimensions you wish to display them and then uploaded to the **images**, **images/medium** and **images/large** directories. If you have hundreds of images, this may seem like a daunting prospect, but it shouldn’t be quite as bad as it sounds. Any decent image-editing application will have some system for batch-processing (carrying out the same actions on multiple files).  

**NOTE:** the basic "images" (thumbnails, normal-size images) should be uploaded via admin in the usual way via the product-edit screen, and then FTP should be used for uploading your `_MED` and `_LRG` images, as mentioned in the preceding paragraph.  

**Optimising images for ZC**  

Start by deciding on the size you want the large image to display at.  

As mentioned earlier, you can’t set the dimensions of the large image in ZC, but it will display at the dimensions you upload it, although you may have to tweak the javascript file for the pop-up window to open at the size you want. The file you need to edit is `/includes/modules/pages/product_info/jscript_main.php`. In the function popupWindow(url) change width= and height= to your sizes. (You can also decide whether or not you want scrollbars by setting scrollbars=no or scrollbars=yes.) Then save the file to `includes/modules/YOURTEMPLATE/pages/product_info/`. 

You shouldn’t choose a size larger than that of the original (if you have to expand it, you’re liable to lose quality). For most purposes, making the large image 400 or perhaps 500 pixels wide should be sufficient although if you’re working from a digital camera, you may want to choose a size that is a direct proportion of the camera output such as 480 or 640.  

In fact, let’s assume you are working with a collection of photographs taken with a digital camera, with a mix of landscape and portrait images. This in itself poses another “problem” in that the layout of your pages will vary slightly depending on whether your image is sideways or upright. For the sake of uniformity throughout your site, I would suggest that you decide on a square image with your photographs re-sized to fit horizontally or vertically as required and the remaining area is just “white space” 
(unless you have a different colour as your background.)  

For this explanation we want the large picture to be either 480 pixels wide or 480 pixels high depending on its orientation so that everything remains in proportion; we want the medium picture to be 240 and the small to be 120\. I’m also assuming that all your images will have unique names – naming is for another tutorial! Having said that, it’s recommended that the large images are called `imagename_LRG.jpg` and medium are called `imagename_MED.jpg` – [graphics editors](/user/first_steps/useful_tools/#graphics-editors) allow renaming of multiple files. They also allow some of the processing below. 

1. Gather all the images in a folder on your hard drive.  
2. Copy all the landscape orientated pics to a new folder (call it **landscape**)  
3. Copy all the portrait orientated pics to another new folder (**portrait**)  
4. Run your image-editor’s batch processor (<font color="red">you’ll have to find out how to do this from your image-editor manual/help files</font>) on the files in the **landscape** folder to re-size them all to the same width (use 480px – and if you are using standard digital photos, this should give you a height of 360)  
5. Repeat the above on the files in the **portrait** folder to re-size them all to the same height (i.e. 480px – should give you a width of 360)  
6. Now run another batch process on the two folders to  
• resize your canvas or paper (depends what your image-editor calls it) to 500 pixels x 500 pixels and set the canvas or paper colour you want with the image centred. (Using a canvas slightly larger than your picture ensures a margin from anything else that may be on the webpage.)  
• Optimize the images for the web  
7. Unless you want to keep them separate you can now combine all the images into one folder called **large** as they are all 500pixels square.  
8. Upload them all to **images/large**  
9. Create another folder called **medium**. Copy all the images from **large** to it. 
10. Run a batch-process on the files in **medium** to resize to 250 pixels square; you may as well optimize for web as well.  
11. Upload them all to **images/medium**  
12. Create another folder called **small**. Copy all the images from **large** to it.  
13. Run a batch-process on the files in **small** to resize to 125 pixels square; you may as well optimize for web as well.  
14. Upload them all to **images**.  

You have now given ZC the best chance of giving your visitors the best visual display at the optimum download time.
