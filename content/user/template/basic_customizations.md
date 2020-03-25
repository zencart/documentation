---
title: Basic Template Customizations 
description: Basic Template Customizations in Zen Cart
category: templates
weight: 10
---

Before you read this article, please be sure you are familiar with 
[Basic Terms](/user/first_steps/basic_terms/) used in describing
Zen Cart files. 

### Can I change the width of the side boxes?
To change the width of the sidebox columns, open [Admin -> Configuration -> Layout Settings](/user/admin_pages/configuration/configuration_layoutsettings/). 

Click the Box Width you wish to change and edit it, the width can be fixed (default is 150px), expressed as a percentage of the total page width or as a relative size (20em). You can also change the width of either column to suit your design.

For example: if you were using a fluid design and wanted the boxes to shrink and grow depending on the window size you would set the columns to 20% and the boxes to 100%.

You can also turn off either column universally in the same section of the admin.

### How can I remove the search box in the header navigation bar?
Open [Admin -> Tools -> Layout Boxes Controller](/user/admin_pages/tools/layout_boxes_controller/). Find `search_header.php`, edit, and turn both switches to off.


### How do I show the Categories on the main page?
Open [Admin -> Configuration -> Layout Settings](/user/admin_pages/configuration/configuration_layoutsettings/). 

Find `Categories - Always Show on Main Page`, click edit and enable the feature.


### Can I remove the "Powered by Zen Cart" from the footer of my cart?
Shops that wish to be listed in the Zen Showcase must leave "Powered by Zen Cart" in the footer for identification. Leaving the "Powered by Zen Cart" is advantageous to both you and Zen Cart because a relevant reciprocal link can help you with search engine rankings. In the event you do not wish to be listed in the Zen Showcase, "Powered by Zen Cart" may be removed, but it may not be changed.

### How do I change the colors and fonts?
Find the file `includes/templates/YOURTEMPLATE/css/stylesheet.css`. Start by opening the style sheet in your favorite text editor:

All of the pages are broken into smaller pieces called "classes" and each class has a style. The class styles are used to control the look of your fonts, colors, text size, borders, background images, etc. Change the colors by substituting standard HTML color numbers for the text and background colors. Change the text size by increasing or decreasing the size, change the typeface by using a different font name.

To remove a CSS element, such as a border, simply comment out the line you don't want to use with a `/*` (slash, asterisk) at the beginning of the line and `*/` (asterisk, slash) at the end of the line. After making your changes upload the stylesheet to the directory, refresh your browser and admire your handywork.

For more information on Cascading Style Sheets search the Internet for links to tutorials and references.

### How do I change the "MyCard" images for Credit Cards?

Zen Cart does not provide credit card images.

You may wish to contact your Merchant services for official images that you are permitted to use.

Once you have obtained the allowed images, upload your new gifs and replace the ones that are holding the place on the pics you see on your checkout page.

If you wish to override the defaults, the images should go here:

`includes/templates/YOURTEMPLATE/images/icons`

```
cc1.gif = Visa
cc2.gif = MC
cc3.gif = Amex
cc4.gif = Diners
cc5.gif = Discover
cc6.gif = JCB
cc7.gif = AustralianBankCard
```

### Where are the buttons and how do I change them?

The list of buttons is in:
`includes/language/english/button_names.php`

Create your buttons using your favorite image editor. The buttons may to be saved as GIF, JPG or PNG. If you are not using the same format or name as the original buttons, edit `button_names.php` and save the edited file in your override directory `includes/language/english/YOURTEMPLATE/button_names.php`.

Upload your button images to:
`includes/templates/YOURTEMPLATE/buttons/YOURLANGUAGE/`

**NOTE:** If you are using multiple languages you need a set of buttons for each language.

Another approach is to use CSS buttons feature. Turn on 
`CSS Buttons` in [Admin->Configuration->Layout Settings](/user/admin_pages/configuration/configuration_layoutsettings/).  If you do this, there is no need
to maintain images for each button; the images are generated in CSS.

### Are there any template overrides in the Admin area?
Up to and including v1.5.6, there are no "overrides" for core files in the Admin area.

If you wish to change admin functionality, you will have to edit the core files directly.   Be sure to keep a list of your changes for quick reference when upgrading.

### What files are used to edit both the way a product displays in the category listing and the product description page?

This is handled in many ways. 
There are administrative "switches" under 
- [Admin-> Configuration-> Layout Settings](/user/admin_pages/configuration/configuration_layoutsettings/) 
- [Admin-> Configuration-> Product Info](/user/admin_pages/configuration/configuration_productinfo/) 
- [Admin-> Configuration-> Product Listing](/user/admin_pages/configuration/configuration_productlisting/) 

There are language files controlling text content.
There are template files controlling the display of the information.

For more specific questions, please go to the [support forum](https://www.zen-cart.com/forumdisplay.php?15-Templates-Stylesheets-Page-Layout) and post a new topic, with as much detail as possible about what you're wanting to do, including a URL if possible.

### How do I to change shopping cart line that shows Weight, Item Count and Price? 

Go to:   [Admin->Configuration->Shipping/Packaging](/user/admin_pages/configuration/configuration_shippingpackaging/).
Select  Display Number of Boxes and Weight Status

Choose the desired setting:

```
0= off
1= Boxes Only
2= Weight Only
3= Both Boxes and Weight
```

### Can I turn off fields from my product info page?
To turn off the weight, inventory count, manufacturer, etc. on my product info page, do the following: 
Go to [Admin > Catalog > Product Types](/user/admin_pages/catalog/product_types/).

Choose Products General (or the product type you are customizing).

Click [Layout Settings](/user/admin_pages/catalog/product_types_edit_layout/) and turn off any settings you do not want to display on the store pages.

### How do I change weight from pounds to Kilograms
In `includes/languages/english.php` 
find the following lines of code:

```
define('TEXT_PRODUCT_WEIGHT_UNIT','lbs');

define('TEXT_SHIPPING_WEIGHT','lbs');
```

Change the highlighted portions, making sure that the single quote marks are not left out.

Save the changed file to `includes/languages/YOURTEMPLATE/english.php` and upload to your server.

### My browser bar says "Zen Cart!, The Art of ...", where do I change that?

To change the title text to say what you want, open the `includes/languages/english/meta_tags.php` file in your text editor. Find the following line of code:

```
// page title
define('TITLE', 'Zen Cart!');

// Site Tagline
define('SITE_TAGLINE', 'The Art of E-commerce');
```

Replace the title and tagline text with your own text, making sure that the single quote marks are not left out and new quote marks are not added.

Save the edited file to `includes/languages/english/YOURTEMPLATE/meta_tags.php` and upload it to your server.

