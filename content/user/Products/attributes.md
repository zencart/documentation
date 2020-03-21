---
title: Attributes - adding to products
category: products
weight: 1
---

There are 3 parts to attributes:  

*   Option Name
*   Option Value
*   Attribute on the product


### Defining Option Names:

`Admin -> Catalog -> Option Name Manager`

**Example:**  

**Color**  

a) Order (This is the sort order the Option Name displays on the screen.)  

b) Select an Option Type:  

*   Dropdown (note when only 1 option value this will automatically be switched to a Radio Button and later when more than one value it will automatically switch to the dropdown)
*   Radio Button
*   Checkbox
*   TEXT (this does not get an Option Value)
*   FILE (This does not get an Option Value)
*   READONLY (this is for **Display Purposes Only** and is not part of a calculation nor does it appear in the Shopping Cart or the Order. It is more or less an Informational Attribute that can be used with 1 to many products and then, later, changed in one place to change on all products.)

On some Option Names, based on the Type.  There are more settings if you Edit the Option Name:  

For Option Type TEXT:  

*   Comments
*   Max Display Size (size of input box on screen)
*   Max Length (max number of characters/spaces)

For Option Type Radio buttons and checkboxes:  

*   There are choices of image layout

### Defining Option Values

`Catalog -> Option Value Manager`

a) Pick the Option Name  
b) Give a Name like Red  
c) Give a default Sort Order  

The sort order is used if you want to globably sort your Option Values to match otherwise you can set these manually per product or later update a product, category or whole store.  

### Attributes Controller

Now you should have made several Option Names like 

*   Color
*   Size
*   etc.

And then set the Option Values for these like:  

*   Red
*   Orange
*   Yellow
*   Green
*   Blue
*   Purple
*   Brown
*   Black
*   White

and  

*   Small
*   Medium
*   Large
*   X-Large
*   X-Small

Using the Default Sort Order on these values will help you later in getting them into a nice display on the product pages.  

Example, to create the Option Values for the Option Name **Color:**  

Option Name Color  
Option Value Red  
Option Sort Order 10  

Option Name Color  
Option Value Orange  
Option Sort Order 20  

Option Name Color  
Option Value Yellow  
Option Sort Order 30  

Option Name Color  
Option Value Green  
Option Sort Order 40  

Option Name Color  
Option Value Blue  
Option Sort Order 50  

Option Name Color  
Option Value Purple  
Option Sort Order 60  

Option Name Color  
Option Value Brown  
Option Sort Order 70  

Option Name Color  
Option Value Black  
Option Sort Order 80  

Option Name Color  
Option Value White  
Option Sort Order 90  

It is also a good idea to make a Default Option Value that the Customer **cannot** add to the cart to force the Customer to make a proper choice with:  

Option Name Color  
Option Value Pick a Color from Below (or something that suits your site best)  
Option Sort Order 0  
Default Attribute to be Marked Selected: YES  
Use for Display Purposes Only: YES  

**Adding the Attributes to the Products**  
So now to add them to the products.  
This is done via the Attributes Controller  

**a) Select a Product to add Attributes to**  
You can look up a product in a couple ways:

- Either pick a Category or a Product  
- When you pick a category, the ones with a `*` have products in them and this will display the first product Previous/Next  
- When you pick a product,  click display, this sets the category to this product's master category id, so you can now use the Previous/Next if you like.  

**b) Add the Attribute Option Name+Value Pairs**  
Once the Product is displayed that you want to add attributes to, go to the Add Attributes box  
- The Product Name should already be selected.  

1\. Now select the Option Name  

2\. Next select a matching Option Value, notice they say what kind of Option Type you have selected.  ie:  Blue [COLOR]  
    You will notice the Option Values say their names and next to them the Option Name that they match to.  

3\. Depending on what you want to do with attributes there are several methods to price, add weight, sort order, and mark the type of attribute this is.  

Price can be entered with a prefix of + or - or blank.  

+ and blank will add the attribute price  
- will subtract the attribute price  

Weight can be entered optionally if it effects the product weight with a prefix of + or - or blank.  

+ and blank will add the attribute weight  
- will subtract the attribute weight  

There are other pricing options also available besides the standard prices.  

*   One Time Charge
*   Price Factor
*   One Time Charge Price Factor
*   Attribute Qty Price
*   One Time Attribute Qty Price
*   For TEXT
*   Price per word and free words
*   Price per letter and free letters

4\. Then there are the Attribute Flags in the colored boxes.  
These are used to help distinguish other features of the attribute such as:  

*   Use for display only (attribute cannot be selected and added to cart. Good for things like "Select from Below" to force the customer to make their own choice and not just hit Add to Cart and get a pink snail instead of a blue snail.
*   Attribute is Free when product is Free (Some products you may set to Free, but the some attributes are free and some attributes cost money.)
*   Default Attribute (Should be used especially on Radio buttons, or if you have an attribute you prefer the customer selects.)
*   Apply Discounts used by Product Sale/Special (this will apply the same type of discount that the product is getting from the products_price vs the special or sale price.)
*   Include in Base Price (when products are priced by attributes mark the attributes include in base price then the lowest price in each Option Name group are added together to make up the product price. NOTE: when not the product is not marked priced by attribute this setting has no effect on the price.)
*   Attribute Required for TEXT (Some text is required text and cannot be left blank by the customer.)

5\. If this attribute is a downloadable file, enter the filename.  

6\. **Be sure to click Add to add the newly-defined Attribute.**  
You can always edit or delete them after adding.  

When done, you can update the sort orders for the product to the Option Value sort order by pressing the button at the top of the page.  

### Downloadable Products

Note: if you plan on using downloads, be sure you have configured your Attribute Settings for the files.  See **Admin -> Configuration -> Attribute Settings**.  

For more information, see [configuring downloadable attributes](/user/products/downloadable/).
