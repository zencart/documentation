---
title: Attributes Controller 
category: admin_pages
weight: 60
---

The Attributes Controller allows you to add [attributes](/user/products/attributes_info/) to your product,
creating a variant product.

Before you can add attributes to your products you need to set option names in [Admin - Catalog - Option Name Manager](/user/admin_pages/catalog/option_name_manager/) 
and give these option values in [Admin - Catalog - Option Value Manager](/user/admin_pages/catalog/option_value_manager/).

Its a good idea to pre plan which attributes you want on which products as you will then know which categories or products to copy attributes to.


## Select a product to add attributes to

*   use the dropdown box to select the category your chosen product is in

*   you then have a choice of how to select your product

    - click *Previous Product* or *Next Product* beside the category dropdown box, or 

    - select your chosen product from the large scroll box and click *Display*.

## Add the Attribute

*   go to the large grey box titled 'Adding New Attributes'

*   select the option name you want to add from the first scroll box

*   select a **matching option value** from the second scroll box

    e.g select option name **Size** [dropdown] from the 1st box and Small [**SIZE:**] from the 2nd box.

*   click *Insert*. 

## Weights and Prices

*   **Price** can be entered with a prefix of + or - or blank
    *   `+` and blank will add the attribute price
    *   `-` will subtract the attribute price
    *   When you Price by Attribute, the price you enter here will be added to your base price, whether you define a + prefix or not.

*   **Weight** can be entered optionally if it effects the product weight with a prefix of + or - or blank
    *   `+` and blank will add the attribute weight
    *  `-` will subtract the attribute weight

![Prices and Weights](/images/attributes_controller_prices.png) 
[Larger Image](/images/attributes_controller_prices.png)

There are other pricing options also available besides the standard prices.
See [Attribute Pricing](/user/products/attribute_pricing/) for an explanation of these options. 

*   One Time Charge - Charge for first item (does not effect prices of subsequent items).
*   Price Factor
*   One Time Charge Price Factor
*   Attribute Qty Price
*   One Time Attribute Qty Price
*   Price Per Word & Free Words
*   Price Per Letter & Free Letters

For TEXT

*   Price per word and free words
*   Price per letter and free letters

**Note:** If you don't see per word and letter pricing, it's because you have turned off [Enable Text Pricing by word or letter](/user/admin_pages/configuration/configuration_attributesettings/#enable_text_pricing_by_word_or_letter) on the Admin > Configuration > Attributes Settings screen.

Similarly, if you don't see the Price Factor fields, it's because you have turned off [Enable Price Factor](/user/admin_pages/configuration/configuration_attributesettings/#enable_price_factor) on the Admin > Configuration > Attributes Settings screen.

### Attribute Quantity Discounts

**Quantity discounts** (_Attributes Qty Price Discount_) are useful when the entire group of products being ordered has a different price if a certain number of them are ordered. _Note_: The price amount specified for a given number of items will be applied to the entire group of items; the price does not get applied to items in steps.

Syntax: configured using [colon-separated pairs](/user/running/colon-separated-pairs/). 

1:11,3:10.00,6:9.00,9:8.00,12:7.00,15:6.00, 45:5.00

<table border="1">

<tr>

<td>QTY</td>

<td>1</td>

<td>2-3</td>

<td>4-6</td>

<td>7-9</td>

<td>10-12</td>

<td>13-15</td>

<td>16+</td>

</tr>

<tr>

<td>PRICE</td>

<td>$11.00</td>

<td>$10.00</td>

<td>$9.00</td>

<td>$8.00</td>

<td>$7.00</td>

<td>$6.00</td>

<td>$5.00</td>

</tr>

</table>

As you can see, the number you enter is the maximum limit of the discount, and the price applied to anything below the number associated with it.

**Onetime Quantity discounts** (_Onetime Attributes Qty Price Discount_) allow specific amounts to be applied to quantity discounts. Example: 400:5 will apply a onetime charge of $5 to an order with any number of items less than 400.

Negative numbers work for in these entries as well, making them quantity discounts or quantity charges. This is useful if you define a base price and would like to allow the user to have the discount off the base price.

**Note:** Don't confuse these **attribute** discounts with [**product** quantity discounts](/user/products/quantity_discounts/), which are set using [Products Price Manager](/user/admin_pages/catalog/products_price_manager/). 

- *Product quantity discounts* show you amounts off according to the size of the order.  
- *Attribute quantity discounts* show you decreasing prices for a particular attribute according to the size of the order. 

**Note:** If you don't see this section of the page, it's because you have turned off [Enable Qty Price Discount](/user/admin_pages/configuration/configuration_attributesettings/#enable_qty_price_discount) on the Admin > Configuration > Attributes Settings screen.

## Attribute Flags 

![Prices and Weights](/images/attribute_flags.png) 
[Larger Image](/images/attribute_flags.png)

These are used to help distinguish other features of the attribute such as:

*   Used For Display Purposes Only - attribute cannot be selected and added to cart. Good for things like "Select from Below" to force the customer to make their own choice and not just hit Add to Cart and get a pink ball instead of a blue ball.

*   Attribute is Free when Product is Free - the attribute will be free if the product is free otherwise prices you've set will apply.

*   Default Attribute to be Marked Selected - sets the attribute as default so it is already selected.

*   Apply Discounts Used by Product Special/Sale - this will apply the same type of discount that the product is getting from the products price vs the special or sale price.

*   Include in Base Price When Priced by Attributes - when products are priced by attributes if this setting is selected then the lowest priced attributes will all be added to the base price of the product and displayed to the customer.

*   Attribute Required for Text or File - means the customer must fill in this field before adding it to the cart.

## Attribute Images

![Prices and Weights](/images/attribute_images.png) 
[Larger Image](/images/attribute_images.png)

To add an image to a product's Option Value, use the file selection tool below the label 'Attributes Image Swatch'.  Click *Choose File* and select the image from your computer.  Be sure the *Remove Image?* is set to *No*.

Click *Update*.

To update an image, click *Choose File*, select the updated image from your computer, then click *Update*.  If you want to remove the previous image from the server, set the *Overwrite Existing Image on Server* to *No*.

click *Update*.

To delete an existing image, select *Yes* for *Remove Image? ...*

click *Update*.

**Note:** If you don't see this section of the page, it's because you have turned off [Enable Attribute Images](/user/admin_pages/configuration/configuration_attributesettings/#enable_attribute_images) on the Admin > Configuration > Attributes Settings screen.

## Downloadable Products As Attributes

![Prices and Weights](/images/downloadable_products.png) 
[Larger Image](/images/downloadable_products.png)

- Enter the filename of the download

- Enter how many days the download will expire

- Enter the maximum number of downloads that can be made

## Copying Attributes to Other Products or Categories

You can copy the attributes from one product to another product or to every product in a category. The attribute images and any other attribute options for price or weight also get copied and can be edited once copied.

At the top of the attributes controller are several self-explanatory buttons to other sections of the admin

the last two are both COPY TO, the first is to a product, the second to a category

*   click COPY TO (product or category depending on your preference)

*   in the large scroll box choose the category or product you want to copy the selected product attributes to

You then have 3 options

*   *   **delete** first, then copy new attributes - this will delete any attributes attached to the products your copying to then it will add the new attributes
    *   **update** with new attribute images/settings/prices, then adds the new attributes
    *   **ignore** and add only new attributes - this will not alter any existing attributes, it will only add new ones

select one of the above and click COPY

the admin will notify you if this has been successful or not at the top of the screen

any questions you have about attributes may have been already answered in the following Zen Cart forum thread

[https://www.zen-cart.com/forum/showthread.php?t=4810](https://www.zen-cart.com/forum/showthread.php?t=4810)

FIXME pull the information from that thread into the Documentation. 
