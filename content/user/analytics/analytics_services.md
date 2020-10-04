---
title: Integrating with Google Analytics 
description: How do I get analytics data for my store?
category: analytics
weight: 10
---

One of the most popular analytics tracking services is Google Analytics. 
Other excellent competing tools include Fathom Analytics and Piwik/Matomo.

## Basic snippet installation
These services will provide you with a "javascript snippet" to insert onto your site.

The simplest way to do this is to create a new file called

`/includes/template/YOURTEMPLATENAME/jscript/jscript_piwik_analytics.js` (or rename for your desired service)

and paste the javascript snippet code inside it.


## Advanced Integration To Provide Calculated Data

If you need to do some data queries or numeric calculations, you will need to change the `.js` extension in the above file to `.php`
and then you can write PHP code intertwined with the javascript code.

Commonly-requested data which you can incorporate is explained in [Integrating Sales/Analytics/Affiliate Tools](/user/analytics/sales_analytics_affiliate_tools/)


## Advanced Google E-Commerce Analytics

An [Advanced Ecommerce Analytics](https://github.com/torvista/zencart-ec-analytics) plugin exists to feed Google's ecommerce-specific analytics data with sales numbers from your store. It may require some custom coding changes to suit your store's unique products, but it's a handy starting point. 

