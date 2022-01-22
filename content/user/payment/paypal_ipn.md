---
title: PayPal/IPN Troubleshooting
description: Resolving problems with PayPal 
category: payment
weight: 10
---

These are things to check if PayPal payments are not working.

---
### Are you getting specific error messages?
See the [PayPal Errors](/user/payment/paypal_errors/) page to investigate.

---
### Are you getting "Whoops?" timeouts when you return to your cart after payment? 

Note: The only PayPal method subject to this issue is PayPal Standard.  It does not apply to PayPal Express or PayPal Payments Pro. 

See the article [Whoops timeouts after payment](/user/payment/payment_whoops_timeouts/). 

---
### Is the PayPal payment option not appearing?
Did you miss any of the configuration steps when [Configuring PayPal in your Store](/user/payment/paypal_express_checkout/)?

---
### Are Transaction Updates From PayPal Not Updating Your Orders?

PayPal sends automatic updates to your store whenever a transaction's status changes. Sometimes those notifications don't arrive, for various technical reasons. The following may help troubleshoot:

These are the common configuration errors causing IPN processing to fail:

1.  If it "was" working, but stopped, make sure PayPal's services are running properly. [PayPal Live Server Status](https://www.paypal-status.com/product/production).
2.  Make sure your site is *not* in [down-for-maintenance mode](/user/running/down_for_maintenance).
3.  Make sure your site does *not* have password-protection via .htaccess in order to get to the "store" area.
4.  Check with your host that the server is able to do outbound TLS connections
5.  Use your browser and go to the Login page of your store. If the page is SSL, do you get any certificate errors in your browser? Test from a couple different computers that you don't normally use. An invalid SSL certificate or one that has errors of any sort, could prevent PayPal from successfully posting the notices to your site.
6.  Try accessing `https://YOURSITE.com/ipn_main_handler.php` with your browser. If you see PHP errors, those will need to be resolved. If you get a white screen, then the first phase of PayPal contacting your site isn't encountering errors. This doesn't mean there aren't any, it just means the initial most obvious steps are working.
7.  There are [communication testing tools available](/user/troubleshooting/communication_issues/). If you are asking for troubleshooting help, please supply the URL to each of these tools after you have installed them on your site, so we can assess the responses they reveal.
8.  Turn on [debug logging](/user/troubleshooting/paypal_debug_logging/) in your PayPal module, and post a link to the zipped log files so they can be analyzed. You'll need to check to be sure that your _/logs_ folder is marked read/write (chmod 755). Then use your [FTP tool](/user/first_steps/useful_tools/#ftp-tools) to access/view those logs and zip-and-upload them for analysis.
9.  Check there is no IP block or firewall to prevent PayPal's servers from talking to your server (your host should check this, and you should check any blocking you may have done via your control panel. Also check .htaccess for any _deny from_ statements and be sure none of them are addresses related to PayPal.
    *   PayPal IP Address List and the IP addresses on PayPal's Go Live Checklist should be in your host's firewall whitelist.  See their website for details. 
    *   For sandbox testing, also open: ipn.sandbox.paypal.com
10.  You may find it helps to Uninstall ("remove") and Re-Install the payment module in Zen Cart admin.
11.  When you use two PayPal accounts to make a simulation, make sure you're using the right account.
12.  Check your PayPal profile settings on [paypal.com](http://paypal.com/): 

*   You need your **Instant Payment Notification preferences** ON

*   Instant Payment Notification URL must be set to a valid address. Normally this is the URL of your site's `ipn_main_handler.php` (i.e.: `https://www.YOURSITE.com/ipn_main_handler.php`). However, if you're running Website Payments Standard on another website, you can leave THAT site's URL there instead, as long as it's actually working properly.

13.  Using your hosting control panel, find the "Error Log" option, and check your server's errorlog entries to see if any attempts to access your site's `ipn_main_handler.php` file are being denied for any reason.
14.  If you have a SEFU or SEO plugin installed, try removing it and testing again. Some are not configured to allow PayPal processing.
15.  If you're using Payflow Pro (or Website Payments Pro UK), check your PayPal Manager area for any IP address restrictions. If you've got it restricted to only accept payment requests from certain IP addresses, make sure your webserver's IP address is in the list. Or clear the list out completely. A call to PayPal tech support can verify whether they have any additional IP addresses recorded that you can't see.
16.  You can check whether PayPal has tried to send you IPN notifications that have failed, and re-send them if needed. In your PayPal account, in the My Account tab, go to the History menu and choose the IPN History option. Tick the relevant boxes and press "Resend selected". If there are many "failed", it's best to start with just checking ONE and attempting Resend. Then check your store to see if it comes through (give it 10-30 minutes). If it doesn't show up in your store, check the IPN debug logs on your server and see what errors have been recorded there.
