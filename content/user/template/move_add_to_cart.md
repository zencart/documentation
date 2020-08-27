---
title: How to rearrange the product info page 
description: Changing the product info page layout
category: template
weight: 10
---

Example: I want to move the Add to Cart box to another place on my product page 

1. You have a page you want to change the structure of.
2. Open the page in your browser.
3. Choose View Source from your browser menu.
4. Scroll down to the section you're bothered about moving. In the case of the add-to-cart button, you'll see this:
5. You need to locate the section that starts with and ends with these tags:

Code:
```
<!--bof Add to Cart Box -->
   <div id="cartAdd">
     Add to Cart: <input type="text" name="cart_quantity" value="1" maxlength="6" size="4" /><br /><br /><input type="hidden" name="products_id" value="1" /><input type="image" src="includes/templates/template_default/buttons/english/button_in_cart.gif" alt="Add to Cart" title=" Add to Cart " />  
   </div>
<!--eof Add to Cart Box-->
```

Note the `<!-- bof Add to Cart Box -->` ('bof' is an abbreviation for "beginning of file") and corresponding end tag: `<!-- eof Add to Cart Box-->`.

6. Simply relocate that section up or down in the file to the place where you want it to appear:

Go find those same tags in the template file (if you search using the [Developers Toolkit](/user/admin/developers_toolkit/), you'll find that it's `tpl_product_info_display.php`) and move that entire section up or down in the file as you desire, noting to NOT put anything between any other existing `<bof>...<eof>` markers.

For example, instead of this:

```
<bof product description>
<eof product description>
<bof add to cart>
<eof add to cart>
```
maybe you want something like this:

```
<bof add to cart>
<eof add to cart>
<bof product description>
<eof product description>
```

Do similarly with other sections as desired.

Then use any necessary CSS alterations to style things as needed.

See also this related FAQ: [How do I determine which files to edit](/user/new_user_topics/what_files/). 

