# How do I add additional images to a product?

## A product owns 1 filename ...

_Note: the_ **_base image name is the original image name loaded for the product._  

**The concept of multiple images is best explained using an example:  
From the Admin, you edit a product and specify an image file called:  
<font color="#ff0000">a_bugs_life.gif</font>  
and put it in the<font color="#ff0000">  
/images/dvd</font> directory via the drop down.  

Now you use your FTP program to upload additional images to <font color="#ff0000">/images/dvd</font>  

*   a_bugs_life_01.gif
*   a_bugs_life_02.gif
*   a_bugs_life_03.gif
*   a_bugs_life_04.gif

I used the numbers so these would load in order, as the additional images are loaded alpha/numeric.  

For the large image (used in popups) I use FTP and upload:  

*   /images/large/dvd/a_bugs_life_01_LRG.gif
*   /images/large/dvd/a_bugs_life_02_LRG.gif
*   /images/large/dvd/a_bugs_life_03_LRG.gif
*   /images/large/dvd/a_bugs_life_04_LRG.gif

For the medium image (used as the main image on the product_info page) I upload via FTP:  

*   /images/medium/dvd/a_bugs_life_MED.gif

NOTE: There is <font color="#ff0000">ONLY ONE ( 1 ) Medium Image</font> used per Product on the Product Info page: (pages named product_info, product_music_info etc.) The naming is related directly to the original image.  

Now you do not need to use subdirectories for loading your images.  

All images can be loaded to:  

*   /images
*   /images/large
*   /images/medium

## Suffixes

You can also change the suffix for Large and Medium from _LRG and _MED to something else or to nothing at all.  

I use the suffixes so when looking at 2000 images I can tell what size I am really looking at just from the name. (Very handy for troubleshooting whether the right image is being loaded.)  

_In a future release, this will be more automated with options for auto-generating the thumb and medium based on dpi, height, width and compression ratio  
For now, it uses the same directories that the auto-generated would use, but you do the FTP manually for the different sizes and additional images._  

## Additional information

Note: the **base image name is the original image name loaded for the product.**  

The suffix of _MED and _LRG is optionally defined but very handy for distinguishing image names from a visual standpoint.  
The medium images are kept in the<font color="#800000">/images/medium</font> directory and the large in the <font color="#ff0000"><font color="#800000">/images/large</font></font> directory  

Additional images can be the base name of the original image plus anything after that. For example:  

**Original Image:** fred.jpg  

All of these are considered additional images because they contain the base image name **<font color="#ff0000">PROVIDED</font>** you are in the <font color="#ff0000">/images</font> directory:  

fredabc.jpg  
fred_73b2.jpg  
fred_01.jpg  
fred_02.jpg  
freddy.jpg  
fredrick.jpg  

The advantage of the numbering on the additional images like: _01 _02 _03 is that they will sort in this order when displayed.  

These images are places in the same directory as the main image such as /images  

The large image match would then go in /images/large or /images/large with the Admin defined suffix added to it of _LRG  

fredabc_LRG.jpg  
fred_73b2_LRG.jpg  
fred_01_LRG.jpg  
fred_02_LRG.jpg  
freddy_LRG.jpg  
fredrick_LRG.jpg  

However ... if using <font color="#ff0000">SUBDIRECTORIES</font> such as <font color="#ff0000">/images/mystuff</font> then you need the underscore ( <font color="#ff0000">_</font> ):  

Original Image: fred.jpg  

All of these are considered additional images because they contain the base image name **<font color="#ff0000">PROVIDED</font>** you are in the <font color="#ff0000">/images/mystuff</font> subdirectory or<font color="#ff0000">/images/dvd</font> or any other subdirectory of /images:  

fred_abc.jpg  
fred_73b2.jpg  
fred_01.jpg  
fred_02.jpg  
fred_dy.jpg  
fred_rick.jpg  

The advantage of the numbering on the additional images like: _01 _02 _03 is that they will sort in this order when displayed.  

These images are places in the same directory as the main image such as <font color="#ff0000">/images/mystuff <font color="#000000">or</font> /images/dvd</font>  

The large image match would then go in <font color="#ff0000">/images/large/mystuff</font> or <font color="#ff0000">/images/large/dvd</font> with the Admin defined suffix added to it of _LRG  

fred_abc_LRG.jpg  
fred_73b2_LRG.jpg  
fred_01_LRG.jpg  
fred_02_LRG.jpg  
fred_dy_LRG.jpg  
fred_rick_LRG.jpg  

While both methods are available with or without the underscore, it is recommended to utilize the underscore to avoid confusion. This also provides more flexibility on the image names. However, if you prefer to do without, both methods are available.  

The use of subdirectories help on speed or directory limits, especially on slower servers or servers with limitations.  

NOTE: not all files show via your FTP program when you get into the 1000s of filenames within a directory.  

### ANOTHER WAY TO LOOK AT IT ...

1) the thumbnail, which is the smaller image, in the /images/ folder.  
2) the "medium" image, which is ONLY used on the Product Info page as the primary product image. And ONLY the first "medium" image is ever used.  
3) the "large" images matching the name patterns of all your thumbnails, which if the thumbnail is clicked, will show the large image.  

- /images/abcd.jpg -- the thumbnail shown in all the category pages and sideboxes  
- /images/medium/abcd_MED.jpg -- the main product image shown on the product page itself  
- /images/large/abcd_LRG.jpg -- the large version of the main product image, which is shown if the medium image is clicked  

- /images/abcd_1.jpg - extra thumbnail shown only on the bottom of the product page  
- /images/large/abcd_1_LRG.jpg - large version of the abcd_1 thumbnail  

- /images/abcd_2.jpg - extra thumbnail shown only on the bottom of the product page  
- /images/large/abcd_2_LRG.jpg - large version of the abcd_2 thumbnail  

- /images/abcd_3.jpg - extra thumbnail shown only on the bottom of the product page  
- /images/large/abcd_3_LRG.jpg - large version of the abcd_3 thumbnail  

### Related topics

a. Attribute images can be added to individual attribute options via Admin -> Catalog -> Option Values  
b. You can edit the _MED and _LRG defined suffixes in Admin->Configuration->Images  

# TIPS

It is wise to **NOT use the following symbols** in your image filenames: 

<font color="#ff0000">**+ [ ] $ ' " \ / ()  **</font>  

Also, in case it's not self-evident, the files have to actually exist on your server. So, if you're selecting the "Use an image on the server" instead of uploading a file directly, and things aren't showing up, then that probably means the image file you specified doesn't actually exist on the server.  

If you wish to bypass the multiple image capability, you have two options, which are explained in the tutorial 
[Turning off Additional Images](customizing/turning_off_additional_images.md).
