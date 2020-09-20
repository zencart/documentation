---
title: Documentation
description: How to use this site 
category: first_steps
weight: 10
---

There's no question about it - your first view of the admin is daunting. So many menus!  What are all these settings!  It can be overwhelming. 

Rather than try to understand it all at once, a better discovery strategy is to focus on the changes you want, and how to implement them.  Use the documentation as your guide. 

**Example 1:** The main page shows a box with the title "New Products For *current-month*." How do I get rid of that? 

Quite often there's a configuration switch that allows you to make this change without needing to modify any code.  Let's see if that holds true in this case.

There is an [All Configs](/user/admin_pages/configuration/all/) link shown at the top of the [storeowner documentation page](/user/).  It shows all the configuration values which can be set under `Admin > Configuration`.  Click this link, and then search on the page it opens for "New Products" and you'll find a setting that looks like this:

<div style="margin-left: 20px;"> 
<div style="font-size: 2rem; font-weight:500; line-height:1.2; margin-bottom:10px;">Show New Products on Main Page</div>

<div class='indent'>Key: <b>SHOW_PRODUCT_INFO_MAIN_NEW_PRODUCTS</b><br />
Path: <b>Configuration > Index Listing</b><br />
Description: Show New Products on Main Page<br />0= off or set the sort order</div>
</div>

So this means that in order to turn the display of new products on the main page off, you must go to the `Configuration > Index Listing`.  In your admin, go to that page.  Find "Show New Products on Main Page", and edit this value, setting it to 0.  

If you now refresh your Storefront page, you'll see the new products are no longer shown. 


**Example 2:** Where do I find the list of supported languages? 

Sometimes you're not sure where to look for something in your admin.
There is a list of [All Admin Menus](/user/admin_pages/menu_sections/) shown at the top of the [storeowner documentation page](/user/).  Click on that link, and then search for "Languages" - you'll see there's a menu item `Localization > Languages`.  If you click the link provided in the All Admin Menus, you'll see the [help for the Localization > Languages page](/user/admin_pages/localization/languages/). 


**Example 3:** How do I show some items on an empty shopping cart page? 

If your empty shopping cart page just shows the message, "Your Shopping Cart is empty," you have the option of adding more content to the page. 

Go to the list of [All Configuration Values](/user/admin_pages/configuration/all/), and search for "empty".  You'll come to a set of four configuration values, starting with "Show New Products on empty Shopping Cart Page."  These configs allow you to show New Products, Featured Products, Specials or Upcoming Products when the shopping cart is empty.  And you can do this all from your admin without needing to change a line of code. 

### Next Steps 

Explore these pages and investigate a topic that is of interest to you: 

- [All Configuration Settings](/user/admin_pages/configuration/all/)
- [All Admin Menus](/user/admin_pages/menu_sections/)
- [Top FAQs](/user/all_time_favorites/) 
- [Learning Trails](/user/first_steps/learning_trails/) 

