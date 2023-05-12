---
title: Salemaker 
category: admin_pages
weight: 130
---

This page allows you to view, add, edit or delete sales. 

[Click here](/user/admin_pages/catalog/salemaker/#usage-tips) for salemaker usage tips. 

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

### Usage Tips

- Always use a dot '.' as the decimal separator for Deduction and Price Range.
- Enter amounts in the same currency as when creating/editing a product.
- In the Deduction fields, you can enter an amount or a percentage to deduct, or a replacement price. (eg. deduct $5.00 from all prices, deduct 10% from all prices or change all prices to $25.00)
- Entering a price range restricts the products that will be affected. (eg. only products from $50.00 to $150.00)
- You must choose the action to take if a product is a special and is subject to this sale:
   - **Ignore Specials Price - Apply to Product Price and Replace Special** - 
The sale deduction will be applied to the regular price of the product. (eg. Regular price $10.00, Specials price is $9.50, Sale Condition is 10%. The product's final price will show $9.00 on sale. The Specials price is ignored.)
   - **Ignore Sale Condition - No Sale Applied When Special Exists** - 
The sale deduction will not be applied to Specials. The Specials price will display independently of the sale. (eg. Regular price $10.00, Specials price is $9.50, Sale Condition is 10%. The product's final price will show $9.50 on sale. The Sale Condition is ignored.)
   - **Apply the Sale Deduction to the Special Price - Otherwise Apply to Price** - 
The sale deduction will be applied to the Special price. A compounded price will be displayed. (eg. Regular price $10.00, Specials price is $9.50, SaleCondition is 10%. The product's final price will show $8.55. An additional 10% off the Specials price.)
- Leaving the Start Date empty will start the sale immediately.
- Leave the End Date empty if you do not want the sale to expire.
- Clicking the red or green status icon on the Salemaker main page to start or stop a sale only works if the Start and End date are not set; otherwise, the sale is automatically started and stopped. 
- Checking a category automatically includes the sub-categories.

