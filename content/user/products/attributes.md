---
title: Attributes - adding to products
description: Creating product variants using attributes
category: products
weight: 10
---

There are three aspects to adding [attributes](/user/products/attributes_info/) to a product:  

*   Option Name: The name of the option
*   Option Value: The values that the option may have
*   Attribute: Assigning the combinations of those option names and values to the product, creating the desired variants


## Defining Option Names

This is done in [Admin > Catalog > Option Name Manager](/user/admin_pages/catalog/option_name_manager/).


**Example:**  

**Color**  

a) Sort Order - determines the order in which multiple Option Names are displayed.  

b) Option Type:  

*   Dropdown (note that a dropdown with only a single value assigned will be displayed as a radio button)
*   Radio Button
*   Checkbox
*   TEXT (this does not have an Option Value)
*   FILE (This does not have an Option Value)
*   READONLY (this is for **Display Purposes Only** and is not part of a calculation nor does it appear in the Shopping Cart or the Order. It is effectively an Informational Attribute that can be used with multiple products to easily make a global change to those products).

On some types of Option Names there are more settings available if you Edit the Option Name:  

For Option Type TEXT:  

*   Comments
*   Max Display Size (size of input box on screen)
*   Max Length (max number of characters/spaces)

For Option Type Radio buttons and checkboxes:  

*   There are choices of image layout

## Defining Option Values

This is done in [Admin > Catalog > Option Value Manager](/user/admin_pages/catalog/option_value_manager/).

a) Select the Option Name  
b) Add a value such as "Red"  
c) Enter a Sort Order  

The sort order is used if you want to globally sort your Option Values to be the same.  If not, you can set these manually per product, or later update a product, category or whole store.


## Default Option Value
When you have Option Names that have more than one Value, it may be a good idea to define a Default Option Value, which will be pre-selected when the product page is first loaded.  If you don't, customers could wind up adding to cart with the first attribute value (size small, for example) and not notice their error until they received an unwanted item.

There are three options for setting a Default:
1. Any valid option could be a default.
2. You could create an option value named **"Please Choose:"** but flag it as *For Display Purposes only* to not allow it to be added to the shopping cart (eg: they must choose another option value from the other values you define).  See [How do I make dropdowns start with "Please Select"](/user/products/please_select/) for more details.
3. You could create an optional option value named **"None"** so the customer can opt out of selecting a value (in this case you **should not** flag the option as *For Display Purposes only* so that a purchase may proceed with the default still selected).



## Example

Now you may have several Option Names such as: 

*   Color
*   Size
*   etc.

with assigned Option Values such as:  

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

Setting a Default Sort Order on these values determines the order of display on the product page. 

For example, to create the Option Values for the Option Name **Color:**  

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

## Assigning Attributes Variants To Products

This is done via the Attributes Controller  

**a) Select the Product**  

Choose a Category. The categories listed with a `*` have products in them. Choosing a category with products will display the first product and the Previous/Next buttons.

Navigate through the category with the Previous/Next buttons or choose a product from the dropdown list.

**b) Add the Attribute Option Name+Value Pairs**  

Once the required Product is selected, go to the Adding New Attributes box  

1\. Select the Option Name.  
This will display all the Option Values defined for that Name.

2\. Select an Option Value to add to the product.  

3\. Edit the parameters associated with the Value.

Price display is determined by the product option [priced by attribute](/user/products/attribute_pricing/#product-priced-by-attributes-vs-attributes-with-prices/). 

Price can be entered with a prefix of + or - or blank.  

 \+ and blank will add the attribute price   
 \- will subtract the attribute price  

Weight can be entered optionally if it effects the product weight with a prefix of + or - or blank.  

 \+ and blank will add the attribute weight  
 \- will subtract the attribute weight  

There are other pricing options also available besides the standard prices,
which are controlled by attribute settings. 

*   One Time Charge
*   Price Factor
*   One Time Charge Price Factor
*   Attribute Qty Price
*   One Time Attribute Qty Price
*   For TEXT
*   Price per word and free words
*   Price per letter and free letters

See [Attributes Controller](/user/admin_pages/catalog/attributes_controller/). 

4\. The Attribute Flags in the colored boxes define behaviours of the attribute such as:  

*   Used for display purposes only (attribute cannot be selected and added to cart).  
 If this is enabled, it forces the customer to choose a different option to the default (which could be "Choose" for example). If this is not enabled, it allows a purchase to be made without selecting a non-default option (a default option may be "None" in this case) i.e. making the attribute optional.  
    Good for things like "Select from Below" to force the customer to make their own choice and not just hit Add to Cart and get a pink snail instead of a blue snail.
*   Attribute is Free when product is Free. Some products you may set to Free, but then some attributes may be free and some attributes not.

*   Default Attribute (shown selected on page first-load) should be used especially with Radio buttons, or if you have an attribute you would prefer the customer to select.
*   Apply Discounts used by Product Sale/Special. This will apply the same type of discount that the product is getting from the products_price vs the special or sale price.
*   Include in Base Price. When products are priced by attributes, attributes marked include in base price are added to the base price. The lowest priced option value is used from each option name.
**NOTE:** when the product is not priced by attribute this setting has no effect on the price.
*   Attribute Required for TEXT. Some text is required text/cannot be left blank by the customer.

5\. If this attribute is a downloadable file, enter the filename.  

6\. **Be sure to click Add to add the newly-defined Attribute.**  
You can always edit or delete them after adding.  

When done, you may update the sort orders for the product to the Option Value default sort order by choosing that Additional Action, at the top of the page..  

### Downloadable Products

Note: if you plan on using downloads, be sure you have configured your Attribute Settings for handling files. See **Admin > Configuration > Attribute Settings**.  

For more information, see [configuring downloadable attributes](/user/products/downloadable/).

### Dependent Attributes 

Dependent attributes are these whose range of values depend on the values of previously set attributes.  For example, the values for Car Model depend on the value of Car Make. 

Zen Cart does not natively support this feature but plugins can provide [dependent attribute](/user/miscellaneous/can_zen_cart/#can-zen-cart-configure-products-with-dependent-attributes) support.

