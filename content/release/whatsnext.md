---
title: What's Next for Zen Cart? 
description: Upcoming changes to Zen Cart 
category: release
weight: 100
layout: docs
noindex: yes
---

{{% construction %}}

## 3.0.0 
- New Feature: <a href="https://github.com/zencart/zencart/discussions/6428">Child Templates</a> will be supported, so that storeowners can more easily determine what has been changed from the base release of a template. 
- Modernization: Zen Cart 3.0 will use Bootstrap 5. 
- Modernization: support for older `define` based language files will be dropped.  Moving forward, only [Array based language files](/dev/languages/158_language_files/) will be supported. 

## 2.2.0 
- Admin: Improvements in Sales Report with Graphs.
- Admin: TinyMCE added as the admin HTML editor. 
- Admin: Added capability to customize the upper right link bar using a notifier. 
- Admin: Fixed - Deprecated "Passing null to parameter #1" log will be created when viewing Admin Packingslip or Admin Invoice.
- Core: Improved handling of `product` table records which do not have associated `products_description` records.
- Core: Improved PHP 8.4 compatibility.
- Core: Typo in notifier name `NOTIFY_ADMIN_INVOICE_HEADERS_AFTER_TAX` corrected.
- Core: Updates to POSM to support [Edit Orders 5.0](https://www.zen-cart.com/downloads.php?do=file&id=2400).
- Core: Password reset via URL (versus emailing a temporary password) is being added to the core.  Credit to forum users Numinix and Retched for inspiration.
- Extras: Curltester now includes REST API endpoints for USPS and PayPal. 
- Storefront: Updated embedded MobileDetect to latest version for `responsive_classic` template.
- Storefront: Updated - Refreshed look for responsive classic template.  See [this repo from contributor chadlly2003](https://github.com/chadlly2003/zencart_responsive_classic_redesign).
- Storefront: Fixed - Customer's wholesale status captured when order is placed.
- Storefront: Fixed - PHP log created when empty shipping quote returned.
- Storefront: Fixed - JavaScript problems can occur when `gv_balance` is null. This is an important fix for JavaScript heavy checkouts (OPC, some payment modules).

## 2.1.0 
Zen Cart 2.1.0 has been released; changes are now listed in [What's New in 2.1.x](/release/whatsnew_2.1.0).

## 2.0.1 
Zen Cart 2.0.1 has been released; changes are now listed in [What's New in 2.0.x](/release/whatsnew_2.0.0.html).
