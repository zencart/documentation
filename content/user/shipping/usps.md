---
title: USPS Setup 
description: Shipping via United States Postal Service 
category: shipping 
weight: 10
---


![USPS shipping](/images/usps.jpeg)

There are two USPS Shipping Modules.
Both are provided as [plugins for Zen Cart](/user/plugins/why_plugins/). 

## Pre-requiste Setup

In your ZenCart admin area, make sure you have a zipcode entered at: Admin > Configuration > Shipping/Packaging > Postal Code. Both versions of the USPS Module (WebTools and RESTful) need this to work.

## WebTools USPS Module

Module Link: [WebTools USPS Shipping Module](https://www.zen-cart.com/downloads.php?do=file&id=1292).

In order to use the USPS module, you need to have a USPS WebTools account registered for access to their production RatesV4 and IntlV2 APIs. You must have a separate WebTools user ID for each web store.

If you have an account with USPS for using shipping assistance, this is not the same as the WebTools user ID needed for the shopping cart.

Here is the [link for registering](https://www.usps.com/business/web-tools-apis/welcome.htm).

Several steps are required to get everything you need; please see the instructions for [Getting USPS Credentials](https://github.com/lat9/usps/wiki/Initial-Install:-Getting-USPS-Credentials).

### Setup WebTools

In your Zen Cart admin area, go to Admin > Modules > Shipping, and click on the USPS shipping module, click Install, and fill out the various configuration information fields.

You must complete all the steps in [Getting USPS Credentials](https://github.com/lat9/usps/wiki/Initial-Install:-Getting-USPS-Credentials) before you will be able to go live.

### Troubleshooting WebTools

The USPS module has a setting called "Debug Mode" which you can configure when you go to Admin > Modules > Shipping > USPS > Edit.  Turning debug on (i.e. to `Email`, `Logs` or `Screen`) will show you the raw responses from the USPS server.

### USPS Password Now Required

The USPS now requires that you enter your password in the config; see [the USPS wiki](https://github.com/lat9/usps/wiki/Forgot-or--Lost-Your-USPS-API-Password%3F) for instructions on retrieval if you have forgotten it.

## RESTful USPS Module

Module Link: [RESTful USPS Shipping Module](https://www.zen-cart.com/downloads.php?do=file&id=2395).

This module is different from the original USPS module in that in order to authenticate in, you must have a [USPS.com account](https://reg.usps.com/entreg/RegistrationAction_input) to sign up for the OAuth API. While a personal account will work, it's strongly recommended that you make a separate account for your business. (Your WebTools Username and Password will **NOT** work with this module.)

After you create your account, you need to set up your "app" to obtain your API credentials. You do this through the [USPS Developer Portal](https://developers.usps.com/). You can follow the [full steps to create your API credentials](https://github.com/retched/ZC-USPSRestful/wiki/Getting-Started#installing) on the USPS RESTful wiki.  This will give you the "USPS API Consumer Key" and "USPS API Consumer Secret" required during the installation phase.

### Documentation
[USPS RESTful Readme](https://htmlpreview.github.io/?https://github.com/retched/ZC-USPSRestful/blob/main/README.html)

### Installation

If you are using the Encapsulated module, meaning you downloaded the zip file and unzipped it to the `zc_plugins` directory, you must activate it in the **Plugin Manager**. To do this, simply visit the Plugin Manager, find the row for the USPS RESTful module, and install it.

If you are using the non-encapsulated version, simply unzip the zip folder into your installation directory as directed in the readme.

### Setting up the RESTful module

In your ZenCart admin area, visit Admin > Modules > Shipping, and click on USPS RESTful module. Click Install and fill out the necessary fields.

You will need to obtain your API Credentials ("USPS API Consumer Key" and "USPS API Consumer Secret") before you will be able to get quotes. (Again, your old WebTools API credentials will NOT work with the RESTful module.)

### Troubleshooting RESTful

Much like the WebTools module, there is a "Debug Mode" that can be used to see what the responses are like from the USPS Server (as well as the raw outgoing requests).

### "Why are there two modules?"

The USPS RESTful module is provided since the original WebTools API from USPS will eventually be deprecated. At the current time, you can continue to use the WebTools module if that still works for you. USPS plans on [deprecating WebTools in 2026](https://github.com/lat9/usps/issues/49).
