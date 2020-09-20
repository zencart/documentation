---
title: Linked Product - what is it? 
description: Showing a product in multiple categories
category: products
weight: 10
---

A linked product is a product that is set up to display in more than one category.

This means that you only have to edit that product in one place in order to have changes take effect everywhere it is displayed.  If you put it on special in one place, it will be on special in the other place/category as well.

Linking also means that you'll not see the same product appear more than once in a given list of products.


If you make a "copy" of a product, instead of linking it, then you will have two distinct and separate products which would require separate editing if you were to make changes later. Specials would affect one and not the other, unless you applied the Special to both individually.  In the case of a copy, you might end up seeing both versions of the product appearing in various product lists.

The copy and link operations are done on the [Admin > Catalog > Categories/Products screen, at the products level](/user/admin_pages/catalog/categories_products/). 

You can also add a product to another category using the [Products to Categories](/user/admin_pages/catalog/products_to_categories/) page. 

The Categories/Products screen described above will show a button in the right sidebar labelled **Multiple Categories Link Manager**.  This button takes you to the Products to Categories screen, with the product pre-selected. 

### Why would you use a Linked Product? 

To make it easier for your customers to discover a specific product, no matter how they navigate your site. 

Let's say that your site sells TVs.  Nothing but TVs.  Seems simple till you think of the amount of listings.  There's the obvious of which manufacturer, size, resolution, and web-ready are just a few.  But,  there are a lot more considerations from the customer's view point.  Does the TV have HDMI inputs?  How many does it have?  Is it compatible as a computer monitor?  Will I need a DisplayPort to HDMI adapter?  What are the audio out capabilities? RCA?  Optical?  Plain 3.5 mini-jack?

In simply thinking that you customer is looking for a particular brand name, you may be losing a sale if you make them go through too many choices.  Sure, they may have wanted something from that manufacturer.  But, if that manufacturer doesn't make the right screen size, you may lose a sale from a frustrated customer who went through every TV only to find that the manufacturer did not make an 80 inch screen.  Using standard screen sizes as Categories can save the customer some time as well.  Did you know that, although most screen sizes are divisible by 5, there is a 32-, 43- and 83-inch size as well?

You can imagine if we had to search through hundreds of TVs to find the one that met our needs.  This is where the Multiple Categories Link Manager comes in.  If the customer's primary objective is to find a set with a particular screen size or resolution, it would be great if I had categories for each of the relevant values for these characteristics. 

The more ways you have to quickly get a customer to their desired product, the easier the sale.

## How Would I Set This Up?
First of all, the obvious creation of a category of the manufacturer.  All the TVs manufactured by that company would be under the company name.  If a customer will only buy from one manufacturer, they may just  stop there.

If they are mainly concerned with finding a TV that's 70 inch, the **_Screen Size_** category with a sub-category of **_70 Inch_** would get them closer to their desired item.  Likewise, a **_Resolution_** category with a sub-category of **_1080p_** would get the customer to that resolution quickly.

Other categories and sub-categories can be utilized as well.  Anything that helps the customer get to the desired product is good practice.

## How to Make It Work
Let's consider a (fictional) TV made by Samsung.  The model for this TV is MX701080, and it has a screen size of 70 inches and a resolution of 1080p. 

We would create a category of **_Samsung_**, but then to provide alternate navigation, we would also create the categories **_Screen Size_** and **_Resolution_**.  

**_Screen Size_** would have a sub-category of **_70 inch_**.  **_Resolution_** would have a sub-category of **_1080p_**.

So your categories hierarchy would look like this: 

```
Samsung
Screen Size 
   70 inch 
Resolution 
   1080p 
```

The product itself is entered in only one place.  Since **_Samsung_** is nearest to the top of the category tree, you would enter the product **_Samsung MX701080_** as the first product in the category.  Be sure to include all information about the item, *_especially_* the information that identifies the other features for which you made categories.  

Locate the product in the Categories and Products menu under **_Samsung_**.  Click on the blue C in the Action block of the Product Listing.  If the item only needed to be copied to one or two other categories, it can be done in the Copy To area BUT, we are going to be in several categories.  Scroll down until the **_Multiple Categories Link Manager_** button appears, and click on that.  This will open up the [Products to Categories](/user/admin_pages/catalog/products_to_categories/) page. 

Scroll down to the **_Linked Categories_** section of the page.

![P2C set linked categories](/images/p2c_set_linked.png) 

If the extra categories were entered correctly, you should see a **_Screen Size > 70 Inch_** option and a **_Resolution > 1080p_** option in the listing.  Ticking both of those will cause the Samsung MX701080 to show up in three places on your site.  

So a customer would see this product hierarchy: 

```
Samsung
   * Samsung MX701080
   * Other Samsung televisions 
Screen Size 
   70 inch 
      * Samsung MX701080
      * Other 70 inch televisions 
Resolution 
   1080p 
      * Samsung MX701080
      * Other 1080p televisions 
```

Although linked products show up in multiple categories, there is only one product record in your database for you to maintain.  This means that any change made to the Samsung MX701080 in the main product category will automatically change all the linked products. 

