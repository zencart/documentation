---
title: Store Manager
category: admin_pages
weight: 10
---

This page allows you to reset various counts and settings in your database.
It also allows you to remove debug logs from your cart.

![Store Manager](/images/store_manager.png)

Actions available in Store Manager are as follows: 

- Update All Products' Attribute Sort Orders: if you decide you want (for example) the Color option to appear before the Size option on the product info screen, you would set the attribute sort order in [Admin > Catalog > Option Name Manager](/user/admin_pages/catalog/option_name_manager/), then use this button. 

- Update ALL Products Price Sorter: The Price Sorter exists so that your listing pages can allow customers to sort by price.  You should use this action after importing price data using a tool like [EasyPopulate](/user/products/easypopulate/), or manipulating prices in the database by hand or any tool other than the admin product/sale/special/pricemanager pages. 
Note that after running "Reset ALL Products Master Categories ID" (below) you should also use the "Update ALL Products Price Sorter." 

- Update Hit Counter: The hit counter is shown in the dashboard of your admin in the Statistics widget, and shows you the number of visitors.

- Reset ALL Products Ordered: The products ordered counter is a field in the products table which counts the number of times a product has been sold.  It is used to build the Bestsellers list in the storefront.  Note that this field is **not used** in the [Products Purchased Report](/user/admin_pages/reports/products_purchased/); that report uses a more accurate (but slower) way of counting product sales. 

- Reset ALL Products Master Categories ID: If your store uses [linked products](/user/products/linked_product/) and you add and delete categories frequently, the master_categories_id field for a product can wind up pointing to a deleted category.  This fixes that problem. 

- Set next order number: If you want to start your order numbers at a higher initial value than 1, or need to bump them for another reason, this is the place to do it. 

- Optimize Database: Databases where large numbers of inserts, updates, and deletes are done can become less efficient over time; running this command will solve this problem.

- Cleanup Debug Log Files: This button will remove all [debug logs](/user/troubleshooting/debug_logs/) in your `/logs` folder.  See [removing debug logs](/user/running/removing_debug_logs/) for more details.

Prior to 1.5.7, there was an option to "Reset ALL Products Viewed." This option was removed because it is unnecessary since the [products viewed](/user/admin_pages/reports/products_viewed/) report now allows filtering by date range.
 
