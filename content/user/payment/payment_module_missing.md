---
title: My Payment Methods aren't showing up during checkout
description: Payment Method problems 
category: payment
weight: 10
---


During checkout, if your payment methods aren't showing up, go into Admin> Modules> Payment and check:

1. Is the payment module Installed? If not, click the Install button on the right-hand infobox.

2. Is it enabled? Some payment modules allow you to turn them on or off by clicking the Edit button and setting the status to true/false, on/off, etc. Some will auto-disable themselves if a fatal condition occurs (such as the gateway account credentials expired).

3. Do you have any Zone Restrictions associated with this payment module? If so, then likely by removing the Zone Restriction from the payment module will allow you to use it during checkout.
    You can use Zone Restrictions to limit which modules show up for different customer-billing-addresses (ie: different countries). To do this requires that you create zones to fully match the zones to your customers' addresses. If you are applying restrictions, always be sure to have at least one payment method WITHOUT any zones added to it, or else there will be customers who cannot go through checkout, and then you'll lose a sale!


