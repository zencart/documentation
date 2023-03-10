---
title: Basics - Store Setup Checklist
description: Things to do when setting up a store 
category: first_steps 
weight: 10
---

## Introduction

After [installation](/user/first_steps/how_do_i_install/), you'll want to address several things to get your basic shop operational. One suggested order of operations is the following:

### Language File setup 
- When English is not your preferred language, you should download, install and setup
a language pack for 
your preferred language from the [Zen Cart Downloads](https://www.zen-cart.com/downloads.php?do=cat&id=6). More details are in the help page for 
[Admin > Localization > Languages](/user/admin_pages/localization/languages/). 

### Checklist

1.  **[Admin > Configuration > My Store](/user/admin_pages/configuration/configuration_mystore/)**
    *   Basis of Product Tax - choose what level tax is calculated at.
    *   Basis of Shipping Tax - choose what level tax is calculated at for shipping.
    *   HTML Editor - select your editor for product descriptions and emails/newsletters.  

2.  **[Admin - Configuration - Email](/user/admin_pages/configuration/configuration_email/)**
    *   If you want to send HTML-based emails, turn on Use MIME HTML When Sending Emails
    *   Set the format of emails for _Admin_ to receive in Email Admin Format
    *   Set the email address and status for all extra emails. These are copies sent to the _Admin_ when various messages are sent to the customer.  

3.  **[Admin - Configuration - Images](/user/admin_pages/configuration/configuration_images/)**
    *   Verify that the image sizes are acceptable for your setup.  

4.  **[Admin - Configuration - GZip Compression](/user/admin_pages/configuration/configuration_gzipcompression/)**
    *   Enable GZip Compression if your server supports it. This makes page display much faster in most cases.  

5.  **[Admin - Configuration - Customer Details](/user/admin_pages/configuration/configuration_customerdetails/)**
    *   Choose whether various components are displayed/requested or not.
    *   If you require authorization for customers to access your store, choose those settings here as well.  

6.  **[Admin - Configuration - Credit Cards](/user/admin_pages/configuration/configuration_creditcards/)**
    *   Choose which cards to enable acceptance for. This does _not_ turn on payment processing, it's just a check for later.  

7.  **[Admin - Modules - Payment](/user/admin_pages/modules/payment/)**
    *   Select and configure any desired payment methods.  

8.  **[Admin - Configuration - Shipping/Packaging](/user/admin_pages/configuration/configuration_shippingpackaging/)**
    *   Verify the Country of Origin.
    *   Set the Postal/ZIP Code (if you don't, your shipping quotes won't work).  

9.  **[Admin - Modules - Shipping](/user/admin_pages/modules/shipping/)**
    *   Select and configure any desired shipping providers.  

10.  **[Admin - Locations/Taxes - Zones Definitions](/user/admin_pages/locations/zones_definitions/)**
     *   Insert applicable tax zones for the regions in which you must collect tax.  

11.  **[Admin - Locations/Taxes - Tax Classes](/user/admin_pages/locations/tax_classes/)**
     *   Create classes for the varying tax combinations you must assign to a product. In most cases, you only require one category.  

12.  **[Admin - Locations/Taxes - Tax Rates](/user/admin_pages/locations/tax_rates/)**
     *   Link tax classes and zones and enter the tax rate for those combinations here.  
     *   If you only charge tax in one zone, and most of your products are taxable, consider [setting a default tax class](/user/taxes/default_tax_class/) for new products. 
13.  **[Admin - Localization - Currencies](/user/admin_pages/localization/currencies/)**
     *   Configure the various currencies your shop will accept/process.  

14.  **[Admin - Localization - Languages](/user/admin_pages/localization/languages/)**
     *   Set up the languages you wish to support in your shop.  

15.  **[Admin - Catalog - Manufacturers](/user/admin_pages/catalog/manufacturers/)**
     *   Enter the manufacturers that your products will be linked to.

### Categories & Products

Now that you've done basic setup, you can enter your categories and products.

**[Admin - Catalog - Categories/Products](/user/admin_pages/catalog/categories_products/)**

*   Add new categories to hold your products - see [category management in admin](/user/products/category_management_admin/). 
*   Add new products within relevant categories - see [product management in admin](/user/products/product_management_admin/).

Note:

*   If you have multiple languages defined, you'll be able to enter product and category names and descriptions in each of your languages.

*   To add images, click on the _Browse_ button beside the category/product image field, and select the file on your computer. Then choose the _upload to directory_ folder to store the image in on your server. If the folder you wish to use isn't there, you'll need to go and create it with your [FTP tool](/user/first_steps/useful_tools/#ftp-tools) first.

### Documenting your Policies 

The key business policies you will need to document have pages set up for you by default; all you need to do is fill them in.  Go to Admin > Tools > Define Pages Editor and flush out these files: 

File | Description | URL
-----|-------------|-----
`define_conditions.php` | your store's [terms and conditions](/user/storefront_pages/conditions/) | index.php?main_page=conditions
`define_privacy.php` | your store's [privacy policy](/user/storefront_pages/privacy/)| index.php?main_page=privacy
`define_shippinginfo.php` | your store's [shipping and returns](/user/storefront_pages/shippinginfo/) policy | index.php?main_page=shippinginfo


