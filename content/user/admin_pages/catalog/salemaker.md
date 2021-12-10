---
title: Salemaker 
category: admin_pages
weight: 130
---

This page allows you to view, add, edit or delete sales. 

Sales are price reductions on one or more **categories** of products, versus [Specials](/user/admin_pages/catalog/specials/), which are price reductions on **individual** products.  See [Salemaker vs Specials](/user/miscellaneous/salemaker_vs_specials/) for more details.

When this page is loaded, sales appear in a list. 

![Salemaker](/images/salemaker_list.png)

The currently selected sale is shown in the sidebar on the right, which provides the ability to edit, delete or copy the sale.

![Salemaker sidebar](/images/salemaker_sidebar.png)

Using the Edit button (or the New Sale button at the bottom of the screen) allows you to configure a sale.  The screen looks like this: 

![Salemaker configuration](/images/salemaker_config.png)

Some things to notice about configuring a sale: 

- The sale may be on one or more categories or the entire store
- The sale may have a start date, a stop date, both or neither
- The sale may only apply to products in a specific price range if desired 
- The sale deduction may be expressed as a percent, dollar off or final price 
- The sale may respond in different ways to products which are already on special

Sales may optionally apply to the attribute prices when products have priced attributes.  When such products are put on sale, the flag **Apply Discounts Used by Product Special/Sale** in the [attributes controller](/user/admin_pages/catalog/attributes_controller/#attribute-flags) determines whether the sale discount is also applied to the attributes price. 

Sales are displayed in your store in by directly reducing the price on the product info page, listing pages, the shopping cart page, and so forth.  To learn more, read about [how sales are handled on the storefront](/user/products/sale_products/). 
