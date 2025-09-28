---
title: Customer Approval 
description: Limiting access to your store
category: orders 
weight: 10
---

Most stores allow customers to visit, browse and buy the same day with no prior approval.  However, it is possible to configure your store with restrictions on this process.

The [Customer Approval Status](/user/admin_pages/configuration/configuration_customerdetails/#customer_approval_status__authorization_pending) setting allows you to set restrictions on customers in three possible ways: 

```
1= Must be Authorized to Browse
```
This means customers are locked out of the store until they are approved. 
This is the highest level of restriction available.  It is suitable for 
"Members-only" stores, or stores which are designed for a company intranet. 

```
2= May browse but no prices unless Authorized
```

This setting allows potential customers to create accounts and look at products,
but not see prices until an administrator approves them.  

```
3= Customer May Browse and May see Prices but Must be Authorized to Buy
```

This setting allows potential customers to create accounts and shop, but not complete transactions until they are approved. 

## Customer Account Activation 
In addition, version 2.2.0 and above of Zen Cart has a feature called Customer Account Activation.  If this feature is enabled using Admin > Configuration > Customers > Account Activation Required?, storefront account creation results in an email being sent to the email address used.  The customer must click the link in this email, or they will not be able to check out.  If the customer does this but subsequently engages in fraud, the account can be disabled and the customer will no longer be able to use it.

![Customer Activation Prompt](/images/activation_prompt.png)

If the customer is known to be good but has trouble finding the email, an admin override may be done by editing the customer and moving the Customers Authorization Status to Approved.

Customers who have not yet been approved will not be able to add items to their carts.  In place of an Add to Cart button, they will see a link to the account approval page. 

![Product Listing Page without Approval](/images/product_listing_not_approved.png) 

Compare this to the product listing page for an approved account: 

![Product Listing Page](/images/product_listing.png)

The product info page is handled similarly, with no add to cart button for unapproved accounts.

Note that using the Customer Account Activation feature puts your store into 
Customer Approval Status "3."  Customers may browse and see prices, but they must login to an approved account to add items to their cart. 
