---
title: PayPal Debug Logging 
description: Getting more information by enabling PayPal logs 
category: troubleshooting 
weight: 10
---

You can enable debug logging of PayPal transaction activity.

The debug logs do NOT contain your PayPal password or API certificate information. This sensitive information is masked so that it cannot be stolen and used unscrupulously.
Further, in the default configuration, there are protections in place to prevent snoops from finding and obtaining your log files, as they are named with some degree of randomness, making it virtually impossible to guess.

1. Go to Admin > Modules > Payment ... and choose your PayPal module (either Standard/IPN or Express Checkout, Payments Pro, etc). Click Edit.

2. Choose "Log to File" for your debug option. (recommend to NOT use log-to-email option, because the emails are harder to isolate.)

3. do some test transactions to simulate the problems you're encountering or reporting.  You should see the logs in your `/logs` folder.

4. Once you've duplicated a problem with logging enabled, grab the log files related to that transaction (ie: look at the date/time on the files) and download and zip them for analysis ... ie: you may be asked to provide a link to where the zip file can be downloaded. You might alternatively post the link directly in the support thread where you're discussing a reported problem.


UNDERSTANDING THE LOG FILES
With Express Checkout and Payments Pro, there are several kinds of log files created:

- PayPal_CURL_xxxxxxxxxxx.log -- there are 3 of these per EC transaction: SetExpressCheckout, GetExpressCheckoutDetails, DoExpressCheckout, or 1 for a Payments Pro transaction.
- paypalwpp_xxxxxxxx.log - there are up to 5 of these per EC transaction, showing individual checkpoints. This is useful in seeing what's going on vs where things are aborting, if at all
- paypaldp_xxxxxxxx.log - there are up to 5 of these per Pro transaction, also showing activity at various checkpoints.

In addition, for all modules (Standard/Express/Pro), there will be another log file created:

- ipn_xxxxxxx.log -- This tracks the steps when an IPN is received ... which happens for all activity in your PayPal account. Zen Cart knows which ones to "use" and which to "ignore".

    The "Standard" module relies on this step to insert orders into your store. If that step doesn't happen or aborts prematurely, then the order won't show. Thus, it's better to use Express Checkout, instead of Standard, for your payments.  For more information, see [PayPal Standard - Potential Problems](/user/payment/paypal_standard/). 

- pdt_xxxxxx.log - this sort of log file might appear if the Standard module is being used and a PDT token has been set.

