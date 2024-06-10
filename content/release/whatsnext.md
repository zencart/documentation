---
title: What's Next for Zen Cart? 
description: Upcoming changes to Zen Cart 
category: release
weight: 100
layout: docs
noindex: yes
---
# :construction: UNDER CONSTRUCTION! :construction:

:stop_sign: <font color="red">PLEASE NOTE: The releases listed below have not yet been finalized, and this document is a work in progress.  <br>
These are goals, not commitments.  Any of the improvements listed here might be delayed beyond the stated target release.</font>

## Future Releases (Not Yet Scheduled) 
- New Feature: <a href="https://github.com/zencart/zencart/discussions/6428">Child Templates</a> will be supported, so that storeowners can more easily determine what has been changed from the base release of a template. 

## 2.2.0 
The improvements targeted for v2.2.0 include:  
- New Feature: The <a href="https://vinosdefrutastropicales.com/product_extra_files/options_stock/readme.html">Products Options Stock</a> plugin will be integrated with Zen Cart.  This feature will help storeowners who have product variants whose stock needs to be tracked (red large t-shirts vs blue medium t-shirts, for example).  It is designed to replace the various "Stock by Attributes" plugins which are currently in use.
    
## 2.1.0 
The improvements targeted for v2.1.0 include:  
- New Feature: The Zen Cart admin will be secured with 
[Multi Factor Authentication](/user/security/multifactor/). 
- Admin: FIXED - Searching for customers from the orders page would occasionally lead to a blank right hand infoBox.
- Admin: FIXED - Selecting coupons on pages other than the first page would occasionally fail.
- Admin: The <a href="/dev/code/template_settings/">template settings file</a> may now be viewed from your admin page.
- Admin: The date of last password change is now shown on the Users page in admin.
- Admin: Product Price fields "Gross" and "Net" have been renamed to "Tax Included" and "Tax Excluded."
- Core: Retired Notifiers and Observers can be set to generate deprecated logs automatically.
- Core: The introduction of the `Product` class continues the modernization of Zen Cart.
- Core: Shipping modules now inherit from ZenShipping base class to reduce code duplication and ensure consistency.
- Core: Zones module now has exception rules notifier.  See <a href="/user/shipping/exceptions/">this page</a> for details on usage.</li>
- Storefront: Additional image matching rules now are enforced more strictly for new installs; see [this page](/user/images/additional_images/#additional-images-filename-matching-rules) for details.  
- Extras: Improved and modernized utilities in the `/extras` folder.

## 2.0.1 
Release 2.0.1 has been delivered; changes are now listed in [What's New in 2.0.x](/release/whatsnew_2.0.0.html).
