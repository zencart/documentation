---
title: Tax Classes
category: admin_pages
weight: 40
---

## Tax Classes Defined

Tax Classes are typically used to differentiate between the type of tax calculations that apply to a given product.

Typical tax classes might include:

*   Taxable Goods
*   Non-Taxable Goods
*   GST-Only

### Creating a Tax Class

If you need another tax class,

1.  Go to `Admin > Locations/Taxes > Tax Classes`
2.  Click New Tax Class 
3.  Enter a title and description
4.  Click Insert

### Setting a Default Tax Class for use when adding new products

When entering new products in the Admin area, it is necessary to select the appropriate tax class for that product. Otherwise taxes won't be calculated appropriately on it during checkout.

1.  First, you need to identify the Tax Class ID number.
    *   Go to `Admin > Locations/Taxes > Tax Classes`
    *   Click Edit
    *   Look at the URL in the browser address bar.
    *   You'll see something that looks like: `&tID=3`
        *   In this case, the ID number is 3
2.  Now set the default for product-entry by going to:
    *   [Admin > Catalog > Product Types](/user/admin_pages/catalog/product_types/) (select the desired product type if other than `Product - General`)
    *   Edit Layout
    *   Click on Product Price Tax Class Default - When adding new products
    *   Enter the number of the tax class ID determined above.

