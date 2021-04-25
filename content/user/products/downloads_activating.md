---
title: Downloads - why do they not activate after checkout? 
description: If downloads are not visible to your customers, check here
category: products
weight: 10
---

## Downloads are not activated until payment has been received.

When your customer pays using a payment module whose configuration is set to "Orders Status: Pending", it means you've requested that all purchases with that module mean you DO NOT yet have the payment.

So, if that is the intended behavior, great! Then once you've verified payment then you need to go in to your admin, click on that order, click on Edit, and scroll down to the bottom and upgrade the order's status from "pending" to "processing". After that time the customer will be able to see their download links by going to their My Account page and clicking on the order.

Automated gateways like Authorize.net can be configured to set the order to "Processing" automatically after the gateway gets a response back that the payment is completed. That's why the status setting is normally already at "processing" for those modules when they're installed. Since the gateway is actually only storing the order when the payment IS received, they can activate the order immediately, meaning the checkout-success page will see the download links. But that only works if you're using a live gateway tied to a merchant account.

It also works fine with the "freecharger" module because the order is free, and thus the download is available immediately because you aren't needing payment before activation. But if your freecharger module's setting is set to "Default" or "Pending" then those purchases will need verification and manual updates as well.
But if you intend to NOT review ANY freecharger purchases, then you can set the freecharger Order Status to Processing so that downloads with it are immediately available.

You also want to check the two `Downloads Controller Order Status Value` settings on [Admin > Configuration > Attribute Settings](/user/admin_pages/configuration/configuration_attributesettings/).  When the order status is between these two values, the customer may download their files (assuming the download is not expired and not too many days have passed since the order - these are also configurable settings). 

## NOTES:
- The product must be configured with a valid download in order for download details to display.
- The working downloadable product must be properly configured BEFORE the order is placed. Edits made to the product *after* the order is placed will not get applied to previous orders.
- See: [How to create downloadable items](/user/products/downloadable/)
- See: [Verifying downloadable items](/user/products/downloadable_verifying/)
