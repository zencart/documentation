---
title: USPS Setup 
description: Shipping via United States Postal Service 
category: shipping 
weight: 10
---

The [USPS Shipping Module](https://www.zen-cart.com/downloads.php?do=file&id=1292) is provided as a [plugin for Zen Cart](/user/plugins/why_plugins/). 

In order to use the USPS module you need to have a USPS WebTools account registered for access to their Rate Calculator API. You must have a separate WebTools user ID for each web store.

If you have an account with USPS for using shipping assistance, this is not the same as the WebTools user ID needed for the shopping cart.

Here is the [link for registering](https://www.usps.com/business/web-tools-apis/welcome.htm).
When registering a new account, after 24-48 government hours you will receive an email from USPS with your user ID and some generic instructions.

## Setup
In your Zen Cart admin area, make sure you have a zip code entered at: Admin > Configuration > Shipping/Packaging > Postal Code.

In your Zen Cart admin area, go to Admin > Modules > Shipping, and click on the USPS shipping module, click Install, and fill out the various configuration information fields.

Call USPS 1-800-344-7779 and ask them to take account out of Test (i.e.: Put it into production mode).

If your module doesn't generate quotes properly after this, call USPS back and make sure they have enabled the RateCalculator on your account profile.

## Troubleshooting Rate Calculations 

The USPS module has a setting called "Debug Mode" which you can configure when you go to Admin > Modules > Shipping > USPS > Edit.  Turning debug on (i.e. to `Email`, `Logs` or `Screen`) will show you the raw responses from the USPS server. 

