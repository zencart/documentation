---
title: Downloads which are not products 
description: Posting PDFs and other free downloads on your site
category: products
weight: 10
---

You may wish to simply provide files (such as PDFs or zips) on your site without requiring the registration and purchase steps associated with paid downloads.

For example, you may wish to provide: 

`https://MYSTORE.com/pdfs/acme_anvil_user_manual.pdf `

or perhaps

`https://MYSTORE.com/zips/acme_manuals.zip`

The recommended method of doing this is as follows:

- Create a new folder at the top level of your cart.  Remember that Zen Cart already comes with `/docs` and `/download` folders, so choose another name.  Common choices are `/pdfs` and `/manuals`, but use whatever makes sense for the content you are providing. 
- Prior to populating the folder, create an `index.html` and `.htaccess` file that limits access in the folder.  You can copy these files from the `/images` folder.  Customize the `.htaccess` as needed to add the filetypes you are serving (e.g. `pdf`).
Note: If you are using Ngnix or another webserver other than Apache, you will have to make the appropriate security changes for that system. 

You may also wish to extend your [store sitemap](/user/storefront_pages/site_map/) to reference either all your PDFs or the most important ones. 


If what you want to do is associate PDFs with specific products, look at the [PDF Attachment in Product Description](https://www.zen-cart.com/downloads.php?do=file&id=1642) plugin.

