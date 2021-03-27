---
title: Integrating with Google Analytics 
description: How do I get analytics data for my store?
category: analytics
weight: 10
---

One of the most popular analytics tracking services is Google Analytics. 
Other excellent competing tools include Fathom Analytics and Piwik/Matomo.

## Basic snippet installation
These services will provide you with a "JavaScript snippet" to insert onto your site.

The simplest way to do this is to create a new file called

`/includes/template/YOURTEMPLATENAME/jscript/jscript_piwik_analytics.js` (or rename for your desired service)

and paste the JavaScript snippet code inside it.

## Google Tag Manager

See [/user/running/external_javascript_services/](/user/running/external_javascript_services/) for information about Tag Manager.


## Advanced Integration To Provide Calculated Data

If you need to do some data queries or numeric calculations, you will need to change the `.js` extension in the above file to `.php`
and then you can write PHP code intertwined with the JavaScript code.

Commonly-requested data which you can incorporate is explained in [Integrating Sales/Analytics/Affiliate Tools](/user/analytics/sales_analytics_affiliate_tools/)


## Advanced Google E-Commerce Analytics

An [Advanced Ecommerce Analytics](https://www.zen-cart.com/downloads.php?do=file&id=1997) plugin exists to feed Google's ecommerce-specific analytics data with sales numbers from your store. It may require some custom coding changes to suit your store's unique products, but it's a handy starting point. 

## Google Adwords Conversion Tracking

A script for tracking Adwords conversions is below. Place the code into a new file at: 
`/includes/modules/pages/checkout_success/jscript_google_adwords_conversion_tracking.php`

Be sure to enter your Adwords conversion_id into the `AW_CONVERSION_ID` line where shown.

```
<?php
define('AW_CONVERSION_ID', ''); // enter your Adwords account conversion_id between the empty quotes.


// abort if AW_CONVERSION_ID not configured 
if (!defined('AW_CONVERSION_ID') || empty(AW_CONVERSION_ID)) return;

// abort if this is a page-reload, to prevent duplicate submissions
if (empty($order_summary)) return;
?>

<!-- Google Code for purchase Conversion Page -->
<script type="text/javascript" title="Google Ad Conversion Tracking">
    var google_conversion_id = "<?php echo AW_CONVERSION_ID; ?>";
    var google_conversion_language = "en_US";
    var google_conversion_format = "1";
    var google_conversion_color = "6633CC";
    <?php if (isset($order_summary['order_total'])) { ?>
    var google_conversion_value = <?php echo $order_summary['order_total'] ?>;
    var google_conversion_currency = "<?php echo $order_summary['currency_code']; ?>";
    <?php } ?>
    var google_conversion_label = "purchase";
</script>
<script src="https://www.googleadservices.com/pagead/conversion.js" title="Google Ad Conversion Tracking JS"></script>
<noscript>
<img height=1 width=1 border=0 src="https://www.googleadservices.com/pagead/conversion/<?php echo AW_CONVERSION_ID; ?>/?value=<?php echo $order_summary['order_total']; ?>&currency_code=<?php echo $order_summary['currency_code']; ?>&label=purchase&script=0">
</noscript>
```
