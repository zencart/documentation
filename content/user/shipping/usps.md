---
title: USPS Setup 
description: Shipping via United States Postal Service 
category: shipping 
weight: 10
---

The [USPS Shipping Module](https://www.zen-cart.com/downloads.php?do=file&id=1292) is provided as a [plugin for Zen Cart](/user/plugins/why_plugins/). 

In order to use the USPS module, you need to have a USPS WebTools account registered for access to their production RatesV4 and IntlV2 APIs. You must have a separate WebTools user ID for each web store.

If you have an account with USPS for using shipping assistance, this is not the same as the WebTools user ID needed for the shopping cart.

Here is the [link for registering](https://www.usps.com/business/web-tools-apis/welcome.htm).

Several steps are required to get everything you need; please see the instructions for [Getting USPS Credentials](https://github.com/lat9/usps/wiki/Initial-Install:-Getting-USPS-Credentials). 

## Setup
In your Zen Cart admin area, make sure you have a zip code entered at: Admin > Configuration > Shipping/Packaging > Postal Code.

In your Zen Cart admin area, go to Admin > Modules > Shipping, and click on the USPS shipping module, click Install, and fill out the various configuration information fields.

You must complete all the steps in [Getting USPS Credentials](https://github.com/lat9/usps/wiki/Initial-Install:-Getting-USPS-Credentials) before you will be able to go live.

## Troubleshooting Rate Calculations 

The USPS module has a setting called "Debug Mode" which you can configure when you go to Admin > Modules > Shipping > USPS > Edit.  Turning debug on (i.e. to `Email`, `Logs` or `Screen`) will show you the raw responses from the USPS server. 
## USPS Password Now Required

The USPS now requires that you enter your password in the config; see [the USPS wiki](https://github.com/lat9/usps/wiki/Forgot-or--Lost-Your-USPS-API-Password%3F) for instructions on retrieval if you have forgotten it.

