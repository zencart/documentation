---
title: What sideboxes are available? 
description: Displaying content on the sides of a desktop view of my store
category: sideboxes
weight: 10
customCss: "/css/sidebox_list.css"
---

You can see all the sideboxes that are available to your store by navigating to [Admin > Tools > Layout Boxes Controller](/user/admin_pages/tools/layout_boxes_controller/). 

The following content shows the sideboxes that come built-in with Zen Cart. 

## Banners 

<br>
<div>
   <div class="img_col"> 
      <img alt="Banners Sidebox" src="/images/sidebox_banner_box.png" />
   </div>
   <div class="notes_col">
      The <strong>banners</strong> sidebox shows what's in the sidebox banner group. 
This can be found in the setting <em>Admin > Configuration > Layout Settings</em> - Banner Display Groups - Side Box. 
      <br><br>
      There are two more banner sideboxes, <strong>banner_box2</strong> and <strong>banner_box_all</strong>, which are configured similarly. 
<ul>
   <li><strong>banner_box2</strong> is just a duplicate of <b>banners</b>, which displays a single banner.</li>
   <li><strong>banner_box_all</strong> can display a random selection from the list of banners.</li>
</ul>
<button type="button" class="btn btn-link" data-toggle="modal" data-target="#banner_box2">- View banner_box2</button><br>
<button type="button" class="btn btn-link" data-toggle="modal" data-target="#banner_boxall">- View banner_boxall</button>
   </div>
</div>

<div id="banner_box2" class="modal fade" tabindex="-1" role="dialog">
  <div class="modal-dialog">
    <div class="modal-content">
        <div class="modal-body">
            <img src="/images/sidebox_banner_box2.png" class="img-responsive">
        </div>
    </div>
  </div>
 </div>

<div id="banner_boxall" class="modal fade" tabindex="-1" role="dialog">
  <div class="modal-dialog">
    <div class="modal-content">
        <div class="modal-body">
            <img src="/images/sidebox_banner_box_all.png" class="img-responsive">
        </div>
    </div>
  </div>
</div>

<br clear="all">
<br>

## Best Sellers 

<br>
<div>
   <div class="img_col"> 
      <img alt="Best Sellers Sidebox" src="/images/sidebox_bestsellers.png" />
   </div>
   <div class="notes_col">
      The <strong>bestsellers</strong> sidebox shows links to the best selling items in your store. 
   </div>
</div>
<br clear="all">
<br>

## Categories 

<br>
<div>
   <div class="img_col"> 
      <img alt="Categories Sidebox" src="/images/sidebox_categories.png" />
   </div>
   <div class="notes_col">
      The <strong>categories</strong> sidebox shows a list of your top level categories and obey the category <em>sort order.</em>
      <br><br>
      The parenthetical numbers after the category names are the number of items in that category.  This may be turned off in <em>Admin > Configuration > My Store > Show Category Counts</em>. The featured, special, new, and all product links can be removed in <em>Admin > Configuration > Layout Settings</em>
      <br><br>
       There is another categories sidebox called <strong>document_categories</strong>, for stores with Document type products. The product type Document may be seen on the screen <em>Admin > Catalog > Product Types</em>. <br>
<button type="button" class="btn btn-link" data-toggle="modal" data-target="#documents_categories"> - View documents_categories</button>
	      </div>
	</div>
<br clear="all">

<div id="documents_categories" class="modal fade" tabindex="-1" role="dialog">
  <div class="modal-dialog">
    <div class="modal-content">
        <div class="modal-body">
            <img src="/images/sidebox_documents_categories.png" class="img-responsive">
        </div>
    </div>
  </div>
</div>

<br clear="all">
<br>

## Currencies 

<br>
<div>
   <div class="img_col"> 
      <img alt="Currencies Sidebox" src="/images/sidebox_currencies.png" />
   </div>
   <div class="notes_col">
      The <strong>currencies</strong> sidebox creates a dropdown selector list showing all the currencies supported by the store.  Selecting a new item from the list changes the pricing to use that currency. 
   </div>
</div>
<br clear="all">
<br>

## EZ-Pages

<br>
<div>
   <div class="img_col"> 
      <img alt="EZ-Pages Sidebox" src="/images/sidebox_ezpages.png" />
   </div>
   <div class="notes_col">
      The <strong>ezpages</strong> sidebox creates a list of the <a href="/user/ezpages/what_are_ezpages/">EZ-Pages</a> in your store, with the title Important Links.
   </div>
	</div>
<br clear="all">
<br>

## Featured Products

<br>
<div>
   <div class="img_col"> 
      <img alt="Featured Products Sidebox" src="/images/sidebox_featured.png" />
   </div>
   <div class="notes_col">
      The <strong>featured_products</strong> sidebox is a random display of featured products. <br>
The <i>[more]</i> link in the header goes to the featured products page.<br>
The <strong>specials</strong> and <strong>new_products</strong> sideboxes work similarly. <br>
   </div>
</div>
<br clear="all">
<br>

## Information

<br>
<div>
   <div class="img_col"> 
      <img alt="Information Sidebox" src="/images/sidebox_information.png" />
   </div>
   <div class="notes_col">
      The <strong>information</strong> sidebox presents links to the <a href="/user/template/define_pages/">define pages</a>. Included are shipping information, privacy, conditions, contact us, gift certificate, coupon, and newsletter unsubscribe. 
   </div>
	</div>
<br clear="all">
<br>

## Languages

<br>
<div>
   <div class="img_col"> 
      <img alt="Language Sidebox" src="/images/sidebox_languages.png" />
   </div>
   <div class="notes_col">
      The <strong>languages</strong> sidebox shows icons for the languages in use in the store. 
   </div>
</div>

<br clear="all">
<br>


## Manufacturers


<br>
<div>
   <div class="img_col"> 
      <img alt="Manufacterers Sidebox" src="/images/sidebox_manufacturers.png" />
   </div>
   <div class="notes_col">
      The <strong>manufacturers</strong> sidebox is a dropdown list of the manufacturers. Selecting an entry from this list will show all that manufacturer's products. (NOTE: Only manufacturers that have products associated with them will be shown in this list. You can link manufacturers to products in your Admin panel.)<br>
       A related sidebox, <strong>manufacturers_info</strong> appears only on the product pages with information about the product's specific manufacturer.<br>
<button type="button" class="btn btn-link" data-toggle="modal" data-target="#manufacturers_info">- View manufacturers_info</button>

   </div>
</div>

<br clear="all">

<div id="manufacturers_info" class="modal fade" tabindex="-1" role="dialog">
  <div class="modal-dialog">
    <div class="modal-content">
        <div class="modal-body">
            <img src="/images/sidebox_manufacturers_info.png" class="img-responsive">
        </div>
    </div>
  </div>
</div>
   
<br clear="all">
<br>

## More Information

<br>
<div>
   <div class="img_col">
      <img alt="More Information Sidebox" src="/images/sidebox_more_information.png" />
   </div>
   <div class="notes_col"> 
      The <strong>more information</strong> sidebox presents links to the other define pages, page_2, page_3 and page_4.  
   </div>
</div>
<br clear="all">
<br>

## New Products

<br>
<div>
   <div class="img_col"> 
      <img alt="New Products Sidebox" src="/images/sidebox_new_products.png" />
   </div>
   <div class="notes_col">
      The <strong>new_products</strong> sidebox is a random display of <a href="/user/products/new_products/">new products</a>. <br>
The <i>[more]</i> link in the header goes to the new products page.<br>
The <strong>specials</strong> and <strong>featured_products</strong> sideboxes work similarly. <br>
   </div>
</div>
<br clear="all">
<br>

## Order History

<br>
<div>
   <div class="img_col"> 
      <img alt="Order History Sidebox" src="/images/sidebox_order_history.png" />
   </div>
   <div>
	   The <strong>order_history</strong> shows a list of previously purchased user products. 
   </div>
</div>
<br clear="all">
<br> 
	

## Product Notifications

<br>
<div>
   <div class="img_col"> 
      <img alt="Product Notifications Sidebox" src="/images/sidebox_product_notifications.png" />
   </div>
   <div class="notes_col">
      The <strong>product_notifications</strong> sidebox allows a customer to subscribe to product notifications that you post using the <a href="/user/admin_pages/tools/newsletter/">Newsletter and Product Notifications Manager</a>. <br>
   </div>
</div>
<br clear="all">

## Reviews

<br>
<div>
   <div class="img_col"> 
      <img alt="Reviews Sidebox" src="/images/sidebox_reviews.png" />
   </div>
   <div class="notes_col">
      The <strong>reviews</strong> sidebox features a random display of reviews. <br>On the product info page, the sidebox changes to a review request called the <b>write_reviews</b> sidebox. <br>
<button type="button" class="btn btn-link" data-toggle="modal" data-target="#write_reviews">- View write_reviews</button>
   </div>
</div>
<br clear="all">
	
<div id="write_reviews" class="modal fade" tabindex="-1" role="dialog">
  <div class="modal-dialog">
    <div class="modal-content">
        <div class="modal-body">
            <img src="/images/sidebox_write_review.png" class="img-responsive">
        </div>
    </div>
  </div>
</div>

<br clear="all">
<br>

## Search

<br>
<div>
   <div class="img_col"> 
      <img alt="Search Sidebox" src="/images/sidebox_search.png" />
   </div>
   <div class="notes_col">
      The <strong>search</strong> sidebox provides an interface to search products in the cart.<br>
A second search sidebox, the <strong>search_header</strong> sidebox, is designed for positioning in the page header. <br>
<button type="button" class="btn btn-link" data-toggle="modal" data-target="#search_header">- View search_header</button>
   </div>
	</div>
<br clear="all">

<div id="search_header" class="modal fade" tabindex="-1" role="dialog">
  <div class="modal-dialog">
    <div class="modal-content">
        <div class="modal-body">
            <img src="/images/sidebox_search_header.png" class="img-responsive">
        </div>
    </div>
  </div>
</div>
<br clear="all">
<br>

## Shopping Cart

<br>
<div>
   <div class="img_col"> 
      <img alt="Shopping Cart Sidebox" src="/images/sidebox_shopping_cart.png" />
   </div>
   <div class="notes_col">
      The <strong>shopping_cart</strong> sidebox lists the items that have been added into the customer's cart.<br>
The <i>[more]</i> link in the header goes to the <a href="/user/storefront_pages/shopping_cart/">shopping cart page</a>.<br>
   </div>
	</div>
<br clear="all">
<br>

## Specials

<br>
<div>
   <div class="img_col"> 
      <img alt="Specials Sidebox" src="/images/sidebox_specials.png" />
   </div>
   <div class="notes_col">
      The <strong>specials</strong> sidebox is a random display of specials. <br>
The <i>[more]</i> link in the header goes to the <a href="/user/storefront_pages/specials/">specials page</a>.<br>
The <strong>featured</strong> and <strong>new_products</strong> sideboxes work similarly. <br>
    </div>
</div>
<br clear="all">
<br>

## Who's Online

<br>
<div>
   <div class="img_col"> 
      <img alt="Who's Online Sidebox" src="/images/sidebox_whos_online.png" />
   </div>
   <div class="notes_col">
      The <strong>whos_online</strong> sidebox shows the number of visitors presently on the site.
	</div>
</div>
<br clear="all">
<br>

