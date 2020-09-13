---
title: Product Types
description: Creating custom products with different data requirements 
category: admin_pages
weight: 10
---

FIXME - page needs attention

A much requested feature in Zen Cart was the ability to have unique information layouts for different types of products. For example a Music Video needs to have different information stored and displayed, compared to say a Garden Bench.

Previously there has been no easy way for a Zen Cart store user to do this without ripping apart the core code. The Product Type system was designed to help alleviate that problem.

Throughout this mini-tutorial we will use the Music Product type 
as an example. It is not in anyway meant to be an exhaustive treatise on implementing your own product type, as this will always depend on exactly what you are trying to implement.

However it should provide enough of an overview to get you started. As ever our support forums at www.zen-cart.com, are always there to help you when you get stuck.

## Database Schema 

The Product Types System uses a number of required, and some @@TODO non-required tables within the Zen Cart database. The required database tables are

*   PRODUCT_TYPES
*   PRODUCT_TYPE_LAYOUT
*   GET_TERMS_TO_FILTER

### PRODUCT_TYPES 

The _PRODUCT_TYPES database is used to track base information relating to the product types currently installed. It consists of 8 fields.

*   type_id
*   type_name
*   type_handler
*   type_master_type
*   allow_add_to_cart
*   default_image
*   date_added
*   last_modified

If you want to add a new product type you need to create a new row in the table. Some sample SQL code is:

<pre class="code"> INSERT INTO `product_types` (`type_id`, `type_name`, `type_handler`, `type_master_type`, `allow_add_to_cart`, 
 `default_image`, `date_added`, `last_modified`) VALUES (NULL, 'Products - Portrait', 'product_portrait', '1', 
 'Y', , '0001-01-01 00:00:00', '0001-01-01 00:00:00');
</pre>

`_type_id_` is an auto\_incrementing field and is used to cross reference the type with other Database Tables used by the PTS.

`_type_name_` is user defined, but you should try and stick with the naming conventions that the core team have decided on. For example, we have Products - General for the standard product, and Product - Music for a product type designed for Music CD's. Then we have Document - General for a basic layout for an information only Document, and Document-Product for a Document that can be sold. These names are used in the drop down that appears in the admin product creation pages.

`_type_handler_` again is user defined and is used to build the URL to the code that actually does the work for the product type. It is best to define this similarly to the type_name. For example if the type_name is Product-Music, the type_handler would be product_music. For compatibility across operating systems you should always stick to lower case for the type_handler. More explanation will be given later as to how the type_handler is used to access the unique code for a given product type.

`_type_master_type_` is used to link product types together. This is mainly used if you want to build separate sideboxes to display a category tree of just certain product types. For example the Document types are linked so that we can provide a sidebox that can be used just to navigate categories containing Document Types.

`_allow_add_to_cart_` - provision is made with this field to create product_types that are for information purpose only, and because of that you do not want to allow the shopper to add them to the cart. The basic Document type is a good example of this.

`_default_image_` is reserved for future usage.

`_date_added_` and `_last_modified_` are for internal code use only.

### PRODUCT_TYPE_LAYOUT 

It has always been possible in Zen Cart using the admin interface to decide which elements of a product's information are displayed. Originally this information was saved in the CONFIGURATION table. However as different product types will have differing types of information, we now use a separate table for product types.

The layout of this table is similar to an entry in the configuration table. The fields are

*   configuration_id
*   configuration_title
*   configuration_key
*   configuration_value
*   configuration_description
*   product_type_id
*   sort_order
*   last_modified
*   date_added
*   use_function
*   set_function

an example here is an entry for the music product type.

<pre> INSERT INTO product_type_layout (configuration_title, configuration_key, configuration_value, 
   configuration_description, product_type_id, sort_order, set_function, date_added) 
   VALUES ('Show Record Company', 'SHOW_PRODUCT_MUSIC_INFO_RECORD_COMPANY', '1', 
   'Display Record Company on Product Info 0= off 1= on', '2', '4', 
   'zen_cfg_select_drop_down(array(array(\'id\'=>\'1\', \'text\'=>\'True\'), 
   array(\'id\'=>\'0\', \'text\'=>\'False\')), ', now());
</pre>

This lets the store admin decide whether the Record Company linked to the music product is shown on the product info page. Of course you would need to code the music product info page to use this value e.g.

<pre>   
if (SHOW_PRODUCT_MUSIC_INFO_RECORD_COMPANY == '1') {
  ?&gt;
   &lt;tr&gt;
     &lt;td class="main" align="center" colspan="2"&gt;
       &lt;?php echo sprintf(TEXT_RECORD_COMPANY_URL, zen_href_link(FILENAME_REDIRECT, 'action=url&goto=' . 
         urlencode($products_record_company_url), 'NONSSL', true, false)); ?&gt;
      &lt;/td&gt;
    &lt;/tr&gt;
   &lt;? php
     } // SHOW_PRODUCT_MUSIC_INFO_URL
</pre>

This is just one example, and you should look at the product info code (and associated entries in the PRODUCT_TYPE_LAYOUT table for more examples.

### GET_TERMS_TO_FILTER 

This table is not strictly part of the core PTS, but is used to handle new filter sideboxes.

Filter sideboxes are used to filter product lists based on some variables.

The main example of this is the manufacturers sidebox. This allows you to filter a product lists based on the manufacturer of the product.

e.g. show all products whose manufacturer is Microsoft.

The music product type adds two filter sideboxes, Record Company and Music Genre.

There is only one field in this table.

*   get_term_name

this is the name of the $_GET variable that is returned by the filter sidebox. The relevance of this will be discussed in more depth when we look at catalog side code for the PTS.

## Admin Code 

In previous versions all code for handling adding categories/products was contained within the _admin/categories.php_ file. To accommodate the PTS this file needs to be split up.

_admin/categories.php_ now deals only with displaying and managing the category tree. It also contains the button for adding a new product. On requesting a new product categories.php will call the file [product handler].php. The [product handler] is the name stored in the product_types database table. e.g product_music.php is the admin handler for the Music Type product.

This handler file is basically a skeleton and in general you can just directly copy the _product.php_ handler to your handler file. Note you will also have to create a corresponding language file.

The product handler page then includes a number of needed files.

The two most important are.

_admin/includes/modules/[handler_name]/collect_info.php_ _admin/includes/modules/[handler_name]/preview_info.php_

again [handler name] is the type_handler entry in the product_types table.

These two files are responsible for actually creating a new entry in the product table and as such will need the most customizing if your product type contains new fields/options for your product type.

`_collect_info.php_` contains the code that is used to collect the product details e.g.

*   product name
*   product description
*   product price
*   etc.

`_preview_info.php_` is used to preview the created product prior to adding it to the database permanently.

Within the _admin/includes/modules_ directories there are an number of other files you can override. By this I mean by adding a file of the same name to your _admin/includes/modules/[handler name]/_ directory, it will be used in preference.

Those files are.

`_update_product.php_`

This code is used to update the various tables to actually add the product to the database. You only need to override this file if your product type requires extra fields to be added to the database.

e.g the Music Type stores Genre Type, and record company in a separate table called product_music_extra, it therefore needs to add code to update.php to make sure information from collect_info.php is added to this table.

`_copy_to_confirm.php_`

This code is used when you ask to copy a product to a?new product. If your product type uses extra tables to store information then you need to add code here to ensure that information is copied to the new product

e.g. the Music Type adds code here to make sure data in products_music_extra table is copied to the new product.

`_delete_product_confirm.php_`

This code is used when you delete a product. You may want to remove information stored in other tables associated with your product type here.

`_move_product_confirm.php_`

This code is used when moving a product between categories, in general there should be no reason to override this file as moves are done using the product_id. However someone somewhere may have use for it.

## Catalog Code 

The changes needed to support a product type in the catalog code are less onerous than _Admin_.

In the main you only need to provide a handler page to show the product_info. To create a new product info page you must first create a new directory _/includes/modules/pages/[handler name]_info_

Initially you should copy all of the files contained within the _includes/modules/pages/product_info/_ directory into your _includes/modules/pages/[handler name]_info/_ directory.

Usually the only file you will need to edit within this directory is _main_template_var.php_

e.g. The Music Type adds code here to load information regarding Music genre, Record Company etc. from the _product_music_extra_ table.

You then need to create a template for the product info page for your Product Type. The template should be placed in _includes/templates/template_default/templates_ or alternatively in _includes/templates/[your template]/templates_ if you want to keep it separate from core code.

The template file should be called

_tpl_[handler name]_info_display.php_, again [handler name] being the same as the entry in the type_handler field of the product_types table.

You will of course have to adjust the template to include any extra information associated with your Product type.

One important point. Within the template generally a number of constants are used to decide if a certain element is displayed. For example in the standard product info page, SHOW_PRODUCT_INFO_QUANTITY if set to 1 will display the quantity in stock. These constants are loaded from the database/product_type_layout table.

It is good practice to create separate constants for each product type within this table. For example the Music type uses SHOW_PRODUCT_MUSIC_INFO_QUANTITY instead of SHOW_PRODUCT_INFO_QUANTITY. This allows admin to set the layouts of different product types separately from each other.

## Filter Side Boxes 

One important addition to the PTS in catalog are sideboxes which can filter a product listing. You may already be familiar with this when using the Manufacturers sidebox. This allows you to restrict a product listing to a specific manufacturer.

The Music type adds two additional filter sideboxes. These are Music Genre and Record Company. If you look at the code say for the Music genre sidebox in includes/modules/sideboxes/music_genre.php you can see that the ID for the music genre selected will be passed in the url as a $_GET variable called music_genre_name. In order for this to be processed correctly we need an automatic way of registering these filter terms. As mentioned earlier in the section on databases you can do this by adding the name of the filter variable to the _get_terms_to_filter_ database table.

