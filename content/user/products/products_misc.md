---
title: Miscellaneous Category, Product and Attribute Questions
description: Using Categories, Products and Attributes in Zen Cart 
category: products 
weight: -1 
---

{{< misc >}} 

---
### How do I disable the numbers beside the category links?

These are the category/inventory counts. 

Go to [Admin -> Configuration -> My Store](/user/admin_pages/configuration/configuration_mystore/). 
Locate the *Show Category Counts* option.  Turn it off.

---
### What does MIXED ON mean? 
On the [product editing page](/user/admin_pages/catalog/categories_products/), 
when the setting `Product Qty Minimum` is greater than 1, the 
setting `Product Qty Min/Unit Mix` is used in determining 
whether the minimum has been met. 

If you have the Minimum set to 36 with `Product Qty Min/Unit Mix` = `Yes`, the "MIXED: ON" status message shows.

Mixed ON means that they can "mix" or match Attributes to build the 36 Minimum setting.  For example, 12 Red 14 Yellow 10 Green meets the minimum restriction of 36. 

Mixed OFF means that they cannot "mix" the Attributes to build the 36 Minimum setting. For example, you must have 36 Red and/or 36 Yellow and/or 36 Green
to meet the minimum restriction of 36

---
### Required Attributes not working 

Problem: When i set a attribute to an item like a color that must be specified and I enable the Required button on the attribute it is letting customers add items to the cart without giving a required attribute.

"Required" is only for "text" input fields. (Hence the description of "Text Required").  However, you can still set a default value for an attribute using one of the techniques described below. 

To force selection of an attribute, there are two options: 

1. Create a "Please Select" option (for dropdowns) 

    a. add an attribute that is Display-Only (ie: a color swatch that says "Please Select a Color").

    b. make it the default.
This forces the customer to choose something "other than" the default (since the "default" is set to "display only").

    **NOTE:** This doesn't work for checkboxes.

2. Set a default value (for radio buttons) 

    a. Go to the [Attributes Controller]() and select the product in question (you will need to select the category, then the product, then press *Display*).  The attributes will be shown below the product. 

    b. Pick the attribute you want to be the default, and press the Edit button on the right side of that attribute.

    c. Set the *Default Attribute to be Marked Selected:* radio button to *Yes*.

    d. Press the *Update* button to save this change. 
 
---
### Pricing includes tax

Problem: My products are being displayed with a different price then I set!? If I set something at $2 it ends up listing at 2.22. I have set that prices should not show with tax, I haven't set any tax rates yet.

Chances are that you have changed your currency settings, and your "default" currency is not set to a value of 1.0.
Please visit Admin->Localization->Currencies and set your default currency to value of 1.0

If this does not work please re-ask your question on the 
[main support forum](https://www.zen-cart.com/forum.php).
and supply a URL where it can be seen in action.
Please also list which version of Zen Cart you are using and which currencies you have installed, which one is the default,  and which languages you have installed.

---
### Is it possible to order fractional quantities? 
There are two setups required in order to allow customers to purchase in quantities less than 1:

1. Change a setting in your admin:  Admin->Configuration->Stock->Product Quantity Decimals :  Set to 2 instead of 0

2. Then individually edit each applicable product's settings to allow minimum units of 0.01 or whatever you need.

---
### Can a product be listed in more than one category?
Yes. If you haven't created it yet, set up the product that you want to be listed in two or more categories. Go to the category in which you put that product (Admin > Catalog > Categories/Products) where you will see a row of icons towards the right, one of which is a white "c" in a blue circle. Click on that and you can copy a product to another category.

There are two types of copy: linked or duplicated. In the former case the product shows in both categories but there's only one instance, so any changes will affect both. In the latter case a new, identical product is created, which can then be changed independently of the original.

---
### Why do my product names show up twice? 
Symptom: Instead of showing a product image thumbnail and the product's name, I'm seeing just the product name, but twice!


Cause: When an image is called there is an ALT tag and that ALT tag is the Product Name, but since you do not have images, in your browser you see the ALT Tag Product Name.  Since they are the same thing, it looks like 2 names.


Solution: Give images to your products.

---
### How do I turn off weight from my product descriptions? 
Firstly let's be clear about the difference between a product listing and product info. When you see a number of products listed together, that's a product listing. For example, the New Products page or a Category Listing page are product listing pages.  When you click on one of the individual products, you will be taken to the product info page.

To turn off weight on the product listings pages, login to your Admin area and then choose [Configuration > Product Listing](/user/admin_pages/configuration/configuration_productlisting/), then select *Display Product Weight* and set it to 0.

You may have spotted the Product Info entry on the Configuration menu and already be there to do the same for product info. STOP.

Product info works differently from product listings. This is because of the flexibility that Zen Cart gives you to define different product types. You may wish, for example, to display a weight for a book, but not for a downloadable pdf. Zen Cart allows you to set them up as different product types and display different information about them.

So where do you go to turn off display of a products weight? Follow
the instructions on [this page](/user/template/basic_customizations/#can-i-turn-off-fields-from-my-product-info-page). 

---
### How do I set up "Music" products for audio-previews?

1. Create your Music Genres
2. Create your Media Types (these are the allowed file-extension types you will use for uploading files)
3. Create your Record Companies
4. Create your Recording Artists

5. Create your music products ... be sure to select the "Product-Music" product-type from the pulldown menu when creating the product.
While entering the product details, you can select the Record Artist, the Record Company, the Genre, etc.

6. Create your media collections using Media Manager .... these are like albums/mixes of songs which can be tied to one or many products.
"Insert" to create a new media collection. Just give it a name, and click Save.
Click "Edit" and now you can add media clips to the collection
Click Browse to select a file stored on your PC, based on the selected media-type.
When you click Add, it will be uploaded to the Media Directory selected in the pulldown menu (by default, this is the "/media" folder on your server).
After each item is uploaded, you can click Edit again to add another clip
If you need to delete a clip, simply click the Delete button next to a given clip
7. With your media collection still selected, click the "Assign to Products" button
Choose a category and product with which you want to associate this media collection
You can assign more than one, simply by selecting, clicking Add, and selecting again, clicking Add, etc.
Collections are not limited to certain categories ... they can be assigned to products in various categories as required.
CAUTION: You need to be sure to ONLY select "product-music" products.  The menus do not restrict you to this, but if you select products which are not music products, then your media collections will not be shown in the store.
8. Now your customers can listen to these clips online prior to purchasing your products.
(You might want to ensure that the clips are only short but appealing sections of the full product, to cut down on bandwidth and theft.)

9. You will need to set up your product Attributes to actually tie the "real" music clips to your products for "Purchase".
There are a couple tutorials on this process: 

- [Setting up downloads for products](/user/products/downloadable/)
- [Adding attributes](/user/products/attributes/)

---
### What is the meaning of the number in "minimum values" and "maximum values" during product-entry?

On the [Admin -> Catalog -> Category/Products](/user/admin_pages/catalog/categories_products/) screen, you can setup a minimum quantity and a maximum quantity as well as the units that they must be ordered in. 

```
Minimum - the minimum number that you can buy for the product  (Default = 1)
Maximum - the Maximum number that you can buy for the product  (Default = 0-Unlimited)
Units - the increment qty that you must buy the product  (Default = 1)
```

If you make it so that the minimum quantity was 12 but had to be ordered in units of 3, then the allowed quantities would be:

12, 15, 18, 21, etc.

These have nothing to do with product quantity in stock.  Inventory On Hand is handled by the "Product Quantity" field elsewhere on the same screen.

---
### How do I add quantity discounts to my products?

[Admin -> Catalog -> Products Price Manager](/user/admin_pages/catalog/products_price_manager/)

- Select the product
- Edit
- click the "add 5 blank discounts" button
- fill in the details
- Update

---
<!-- please keep this at the end --> 
{{< faq_questions >}}
