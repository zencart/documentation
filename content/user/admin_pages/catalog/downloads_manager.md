---
title: Downloads Manager 
category: admin_pages
weight: 70
---

This page allows you to view and edit downloadable items. 

![Downloads Manager](/images/downloads_manager.png) 

Each downloadable file is shown, along with its product and attribute combination.  This allows you to easily determine which download is associated with which product.  The small circle next to the filename indicates whether this file is in the expected place (the `DIR_FS_DOWNLOAD` folder). 

A sidebar to the right of each file allows you to easily edit the attributes or the product.  

![Downloads Manager](/images/downloads_manager_sidebar.png) 

It also allows you to quickly reset the associated filename for a download, or its limitation on available days and downloads. 

![Downloads Manager](/images/downloads_manager_sidebar_edit.png) 

Downloadable items will appear on this page once you have 
[created downloadable products](/user/products/downloadable/). 

## Downloads Manager Legend 

At the top left side of the screen, there are three traffic light indicators.  The one you want to see next to the download filename in the Filename column is the green one; the others indicate problems. 

- Yellow (Downloadable Product is misconfigured) - generally this means you have marked your download as Always Free Shipping or Virtual, which you should not.  See [Additional Notes about Downloads](/user/products/downloadable/#additional-notes-about-downloads-and-shipping-costs).
- Red (Missing filename) - this means the filename you specified for the download does not exist in the folder you have specified for storing your downloads.  By default, this folder is `/download`, but [it can be moved](/user/security/relocate_download_folder/). 
