---
title: Basic Template Customizations 
description: What are the most common template changes people do first? 
category: template
weight: -1 
---

Before you read this article, please be sure you are familiar with 
[Basic Terms](/user/first_steps/basic_terms/) used in describing
Zen Cart files. 

---

{{< misc >}} 

--- 

## Can I change the width of the side boxes?
To change the width of the sidebox columns, open [Admin > Configuration > Layout Settings](/user/admin_pages/configuration/configuration_layoutsettings/). 

Click the Box Width you wish to change and edit it, the width can be fixed (default is 150px), expressed as a percentage of the total page width or as a relative size (20em). You can also change the width of either column to suit your design.

For example: if you were using a fluid design and wanted the boxes to shrink and grow depending on the window size you would set the columns to 20% and the boxes to 100%.

You can also turn off either column universally in the same section of the admin.

---

## How can I remove the search box in the header navigation bar?
Open [Admin > Tools > Layout Boxes Controller](/user/admin_pages/tools/layout_boxes_controller/). Find `search_header.php`, edit, and turn both switches to off.

--- 

## How do I show the Categories on the main page?
Open [Admin > Configuration > Layout Settings](/user/admin_pages/configuration/configuration_layoutsettings/). 

Find `Categories - Always Show on Main Page`, click edit and enable the feature.

---

## Can I remove the "Powered by Zen Cart" from the footer of my cart?
Yes.  Keeping this link is not required.  

---

## How do I change the colors and fonts?
Find the file `includes/templates/YOURTEMPLATE/css/stylesheet.css`. Start by opening the style sheet in your favorite text editor:

All of the pages are broken into smaller pieces called "classes" and each class has a style. The class styles are used to control the look of your fonts, colors, text size, borders, background images, etc. Change the colors by substituting standard HTML color numbers for the text and background colors. Change the text size by increasing or decreasing the size, change the typeface by using a different font name.

To remove a CSS element, such as a border, simply comment out the line you don't want to use with a `/*` (slash, asterisk) at the beginning of the line and `*/` (asterisk, slash) at the end of the line. After making your changes upload the stylesheet to the directory, refresh your browser and admire your handywork.

For more information on Cascading Style Sheets search the Internet for links to tutorials and references.

Note that the [Bootstrap template](/user/template/bootstrap/) includes an admin accessible utility called [ZCA Bootstrap Colors](/user/template/bootstrap/#colors-in-the-bootstrap-template), which allows you to modify most template colors from the admin.

---

## How do I change the "MyCard" images for Credit Cards?

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

---

## Where are the buttons and how do I change them?

Newer templates do not use static button images; instead, they use 
[CSS buttons](/user/template/buttons/) feature, which uses CSS to style the text as a button.  
The text used is the alt text for each image button, defined in the language files.

Note that in the case of a Submit button, the text allowed is limited to 30 characters: if this is exceeded the image is used instead.

To use CSS Buttons, enable them in 
[Admin > Configuration > Layout Settings](/user/admin_pages/configuration/configuration_layoutsettings/#css_buttons).  

If you wish to use static images for buttons, refer to the list of buttons in the file 
`includes/language/english/button_names.php`.

Create your buttons using your favorite [image editor](/user/first_steps/useful_tools/#graphics-editors). The buttons may to be saved as GIF, JPG or PNG. If you are not using the same format or name as the original buttons, you will have to override the list of button names as shown below, and make changes to your override copy of the file. 

### Overriding button name list - 1.5.8 and above
Edit `includes/language/english/YOURTEMPLATE/lang.button_names.php`.  (Copy `includes/languages/english/lang.button_names.php` to your override directory `includes/language/english/YOURTEMPLATE/lang.button_names.php` if the override file doesn't already exist.)

### Overriding button name list - 1.5.7 and below 
Edit `includes/language/english/YOURTEMPLATE/button_names.php`.  (Copy `includes/languages/english/button_names.php` to your override directory `includes/language/english/YOURTEMPLATE/button_names.php` if the override file doesn't already exist.)

Then finally upload your button images to:
`includes/templates/YOURTEMPLATE/buttons/YOURLANGUAGE/`

**NOTE:** If you are using multiple languages you need a set of buttons for each language.


---

## Are there any template overrides in the Admin area?
At this time, there are no "overrides" for whole pages in the Admin area.

If you wish to change admin functionality, you will have to edit the core files directly.   Be sure to keep a list of your changes for quick reference when upgrading.

There are many Notifier/Observer hooks available to augment existing functionality, and several auto-loading directories allow plugins to integrate as well. Since v1.5.7 plugins for the Admin can be packaged without having to touch admin files in many cases.

---

## What files are used to edit both the way a product displays in the product listing and the product description page?

This is handled in many ways. 
There are administrative "switches" under 

- [Admin > Configuration > Layout Settings](/user/admin_pages/configuration/configuration_layoutsettings/) 
- [Admin > Configuration > Product Info](/user/admin_pages/configuration/configuration_productinfo/) 
- [Admin > Configuration > Product Listing](/user/admin_pages/configuration/configuration_productlisting/) 

There are language files controlling text content.
There are template files controlling the display of the information.

For more specific questions, please go to the [support forum](https://www.zen-cart.com/forumdisplay.php?15-Templates-Stylesheets-Page-Layout) and post a new topic, with as much detail as possible about what you're wanting to do, including a URL if possible.

---

## How do I to change shopping cart line that shows Weight, Item Count and Price? 

Go to:   [Admin > Configuration > Shipping/Packaging](/user/admin_pages/configuration/configuration_shippingpackaging/).
Select  Display Number of Boxes and Weight Status

Choose the desired setting:

```
0= off
1= Boxes Only
2= Weight Only
3= Both Boxes and Weight
```

---

## Can I turn off fields from my product info page?
To turn off the weight, inventory count, manufacturer, etc. on my product info page, do the following: 
Go to [Admin > Catalog > Product Types](/user/admin_pages/catalog/product_types/).

Choose `Product - General` (or the product type you are customizing).

Click [Layout Settings](/user/admin_pages/catalog/product_types_edit_layout/) and turn off any settings you do not want to display on the store pages.

---

## How do I change weight from pounds to Kilograms

### Using Kilograms - 1.5.8 and above 
Edit `includes/languages/YOURTEMPLATE/lang.english.php`. (Copy `includes/languages/lang.english.php` to `includes/languages/YOURTEMPLATE/lang.english.php` if the override file doesn't already exist.)

Find the following lines of code:

```
    'TEXT_PRODUCT_WEIGHT_UNIT' => ' lbs',
...
    'TEXT_SHIPPING_WEIGHT' => ' lbs',
```

Change the highlighted portions, making sure that the single quote marks are not left out.

### Using Kilograms - 1.5.7 and below
Edit `includes/languages/YOURTEMPLATE/english.php`.  (Copy `includes/languages/english.php` to `includes/languages/YOURTEMPLATE/english.php` if the override file doesn't already exist.)

Find the following lines of code:

```
define('TEXT_PRODUCT_WEIGHT_UNIT','lbs');

define('TEXT_SHIPPING_WEIGHT','lbs');
```

Change the highlighted portions, making sure that the single quote marks are not left out.

---

## My browser bar says "Zen Cart!, The Art of ...", where do I change that?

To change the title text to say what you want, do the following:

### Changing Title - 1.5.8 and above
Edit `includes/languages/english/YOURTEMPLATE/lang.meta_tags.php`.  (Copy `includes/languages/english/lang.meta_tags.php` to `includes/languages/english/YOURTEMPLATE/lang.meta_tags.php` if the override file doesn't already exist.)  

Find the following line of code:

```
    'TITLE' => 'Zen Cart!',
    'SITE_TAGLINE' => 'The Art of E-commerce',
```

Replace the title and tagline text with your own text, making sure that the single quote marks are not left out and new quote marks are not added.

### Changing Title - 1.5.7 and below 
Edit `includes/languages/english/YOURTEMPLATE/meta_tags.php`.  (Copy `includes/languages/english/meta_tags.php` to `includes/languages/english/YOURTEMPLATE/meta_tags.php` if the override file doesn't already exist.)  

Find the following line of code:

```
// page title
define('TITLE', 'Zen Cart!');

// Site Tagline
define('SITE_TAGLINE', 'The Art of E-commerce');
```

Replace the title and tagline text with your own text, making sure that the single quote marks are not left out and new quote marks are not added.

---
<!-- please keep this at the end --> 
{{< faq_questions >}}
