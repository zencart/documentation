---
title: Creating a Customer Account
description: Creating an account on behalf of a Customer in Zen Cart 
category: Running
weight: 10
---

There are several ways to create an account.  The simplest is to go to the storefront and click the login link.  From there, you can create an account with their email address and a randomly chosen password.

If you wish to create accounts from your admin, several options are available: 

- [Add Customers from Admin by balihr](https://github.com/zenexpert/add-customers)
- [Add Customers from Admin by dbltoe](https://www.zen-cart.com/downloads.php?do=file&id=2445)
- [Add Customers from Admin for 1.5.x by lat9](https://www.zen-cart.com/downloads.php?do=file&id=1477)

A feature comparison between the two newer plugins is provided below: 


## Feature comparison

| | zenexpert/add-customers 4.0.0 | dbltoe/admin_add_customer v1.2.3 |
|---|---|---|
| Plugin dir | `zc_plugins/AddCustomers/4.0.0` | `zc_plugins/AdminAddUser/v1.2.3` |
| Authors | lat9, ZenExpert | dbltoe (based on lat9's mod) |
| ZC compatibility | v2.0.0, v2.0.1, v2.1.0 | v2.0.0 → v3.0.0-track `master` |
| Fields collected | Full profile: gender, DOB, company, street, suburb, city, state/zone, postcode, country, phone, fax, email format, newsletter, referral code | Minimal: first/last name, email, phone (optional), tax number |
| Address record | Real address written to `address_book`, set as default | Stub `address_book` row (empty street/city/postcode, zone/country filled just to avoid core warnings) — customer supplies the real one later |
| Account state | Live immediately; authorization from `CUSTOMERS_APPROVAL_AUTHORIZATION` | Created as auth `3` (no-purchase), flips to `0` only after the customer clicks the activation link |
| Activation flow | None | Yes — own `admin_add_user_tokens` table, 64-hex `random_bytes` token, configurable expiry (default 24h), single-use, plus a storefront page (`admin_add_user_activate`) |
| CSV columns | 18: email, names, dob, gender, company, street, suburb, city, state, postcode, country, phone, fax, newsletter, send_welcome, zone_id, group pricing | 6: first_name, last_name, email, telephone, customers_group_pricing, wholesale_level |
| CSV import modes | Two: "valid rows only" vs. all-or-nothing | Single validate-and-insert pass |
| Validation depth | Heavy — postcode formats (US/UK/CA), phone, DOB across 8 date formats, min-length configs | Light — field lengths, email, wholesale numeric |
| Group pricing | Yes | Yes |
| Wholesale (`customers_whole`) | No | Yes — extra wholesale-level field, tax-number field, wholesale-specific signup PDF |
| Resend welcome email | Yes, with optional password regeneration | Yes — regenerates the activation token too, optional password reset |
| Email extras | Coupons, gift vouchers, admin copy | Same, plus an **uploadable header/banner image** for the welcome email and a summary of assigned pricing group/wholesale tier |
| Housekeeping | — | **Delete abandoned signups** — purges customers created before a given date who never filled in street+postcode, cascading to basket/token rows |
| Printables | — | Ships signup-form PDFs (standard + wholesale) for paper collection at events |
| AJAX | Yes — country change repopulates state dropdown/text field | Not needed (no address fields) |
| Docs/extras | Code only, no README | readme.md/readme.html, CSV format guide, good/bad example CSVs, screenshots |
| Repo activity | 1 commit, no README, no description | 13 commits, documented |
