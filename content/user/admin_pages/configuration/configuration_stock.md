---
title: Configuration ≫ Stock
category: admin_pages
weight: 80 
---

The stock configuration settings control stock management as well as various things on the shopping cart page.

<h2 id="check_stock_level">Check stock level</h2>

<div class='indent'>Key: <b>STOCK_CHECK</b><br />
Path: <b>Configuration > Stock</b><br />
Description: Check to see if sufficient stock is available</div>


<h2 id="subtract_stock">Subtract stock</h2>

<div class='indent'>Key: <b>STOCK_LIMITED</b><br />
Path: <b>Configuration > Stock</b><br />
Description: Subtract product in stock by product orders</div>


<h2 id="allow_checkout">Allow Checkout</h2>

<div class='indent'>Key: <b>STOCK_ALLOW_CHECKOUT</b><br />
Path: <b>Configuration > Stock</b><br />
Description: Allow customer to checkout even if there is insufficient stock</div>


<h2 id="mark_product_out_of_stock">Mark product out of stock</h2>

<div class='indent'>Key: <b>STOCK_MARK_PRODUCT_OUT_OF_STOCK</b><br />
Path: <b>Configuration > Stock</b><br />
Description: Display something on screen so customer can see which product has insufficient stock</div>


<h2 id="stock_reorder_level">Stock Re-order level</h2>

<div class='indent'>Key: <b>STOCK_REORDER_LEVEL</b><br />
Path: <b>Configuration > Stock</b><br />
Description: Define when stock needs to be re-ordered</div>


<h2 id="products_status_in_catalog_when_out_of_stock_should_be_set_to">Products status in Catalog when out of stock should be set to</h2>

<div class='indent'>Key: <b>SHOW_PRODUCTS_SOLD_OUT</b><br />
Path: <b>Configuration > Stock</b><br />
Description: Show Products when out of stock<br /><br />0= set product status to OFF<br />1= leave product status ON</div>


<h2 id="disabled_product_status_for_search_engines">Disabled Product Status for Search Engines</h2>

<div class='indent'>Key: <b>DISABLED_PRODUCTS_TRIGGER_HTTP200</b><br />
Path: <b>Configuration > Stock</b><br />
Description: When a product is marked Disabled (status=0) but is not deleted from the database, should Search Engines still show it as Available?<br>eg:<br>True = Return HTTP 200 response<br>False = Return HTTP 410<br>(Deleting it will return HTTP 404)<br><b>Default: false</b></div>


<h2 id="show_sold_out_image_in_place_of_add_to_cart">Show Sold Out Image in place of Add to Cart</h2>

<div class='indent'>Key: <b>SHOW_PRODUCTS_SOLD_OUT_IMAGE</b><br />
Path: <b>Configuration > Stock</b><br />
Description: Show Sold Out Image instead of Add to Cart Button<br /><br />0= off<br />1= on</div>


<h2 id="enable_disabled_product_by_available_date">Enable disabled product by available date</h2>

<div class='indent'>Key: <b>ENABLE_DISABLED_UPCOMING_PRODUCT</b><br />
Path: <b>Configuration > Stock</b><br />
Description: How should disabled products with a future available date be made active when the date is reached?<br /></div>


<h2 id="product_quantity_decimals">Product Quantity Decimals</h2>

<div class='indent'>Key: <b>QUANTITY_DECIMALS</b><br />
Path: <b>Configuration > Stock</b><br />
Description: Allow how many decimals on Quantity<br /><br />0= off</div>


<h2 id="show_shopping_cart__delete_checkboxes_or_delete_button">Show Shopping Cart - Delete Checkboxes or Delete Button</h2>

<div class='indent'>Key: <b>SHOW_SHOPPING_CART_DELETE</b><br />
Path: <b>Configuration > Stock</b><br />
Description: Show on Shopping Cart Delete Button and/or Checkboxes<br /><br />1= Delete Button Only<br />2= Checkbox Only<br />3= Both Delete Button and Checkbox</div>


<h2 id="show_shopping_cart__update_cart_button_location">Show Shopping Cart - Update Cart Button Location</h2>

<div class='indent'>Key: <b>SHOW_SHOPPING_CART_UPDATE</b><br />
Path: <b>Configuration > Stock</b><br />
Description: Show on Shopping Cart Update Cart Button Location as:<br /><br />1= Next to each Qty Box<br />2= Below all Products<br />3= Both Next to each Qty Box and Below all Products</div>


<h2 id="show_new_products_on_empty_shopping_cart_page">Show New Products on empty Shopping Cart Page</h2>

<div class='indent'>Key: <b>SHOW_SHOPPING_CART_EMPTY_NEW_PRODUCTS</b><br />
Path: <b>Configuration > Stock</b><br />
Description: Show New Products on empty Shopping Cart Page<br />0= off or set the sort order</div>


<h2 id="show_featured_products_on_empty_shopping_cart_page">Show Featured Products on empty Shopping Cart Page</h2>

<div class='indent'>Key: <b>SHOW_SHOPPING_CART_EMPTY_FEATURED_PRODUCTS</b><br />
Path: <b>Configuration > Stock</b><br />
Description: Show Featured Products on empty Shopping Cart Page<br />0= off or set the sort order</div>


<h2 id="show_special_products_on_empty_shopping_cart_page">Show Special Products on empty Shopping Cart Page</h2>

<div class='indent'>Key: <b>SHOW_SHOPPING_CART_EMPTY_SPECIALS_PRODUCTS</b><br />
Path: <b>Configuration > Stock</b><br />
Description: Show Special Products on empty Shopping Cart Page<br />0= off or set the sort order</div>


<h2 id="show_upcoming_products_on_empty_shopping_cart_page">Show Upcoming Products on empty Shopping Cart Page</h2>

<div class='indent'>Key: <b>SHOW_SHOPPING_CART_EMPTY_UPCOMING</b><br />
Path: <b>Configuration > Stock</b><br />
Description: Show Upcoming Products on empty Shopping Cart Page<br />0= off or set the sort order</div>


<h2 id="show_notice_of_combining_shopping_cart_on_login">Show Notice of Combining Shopping Cart on Login</h2>

<div class='indent'>Key: <b>SHOW_SHOPPING_CART_COMBINED</b><br />
Path: <b>Configuration > Stock</b><br />
Description: When a customer logs in and has a previously stored shopping cart, the products are combined with the existing shopping cart.<br /><br />Do you wish to display a Notice to the customer?<br /><br />0= OFF, do not display a notice<br />1= Yes show notice and go to shopping cart<br />2= Yes show notice, but do not go to shopping cart</div>


