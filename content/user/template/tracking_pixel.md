---
title: Adding a tracking pixel 
description: Integrating with systems that use tracking pixels 
category: template
weight: 10
---

FIXME please verify 

## Situation:

You've just signed up with an affiliate system who's promised you the ultimate in statistics tracking, commission handling, referral monitoring, and more.  

They've given you a snippet of code and instructed you to place it on your site, after replacing some parameters with actual values of orders in your store. 
But you don't know where to put this new code.  

## Solution:

1\. First, you need to make sure you have an appropriate override file in place.  

THERE ARE TWO OPTIONS:  
a) JavaScript file (recommended)  
To do it with a JavaScript file, simply create the following file:  
/includes/modules/pages/checkout_success/jscript_myaffiliate_program.php  

b) template file:  
To do it with a template file, you'll need the following file on your server: /includes/templates/YOURTEMPLATE/checkout_success/tpl_footer.php (replacing YOURTEMPLATE with the name of your actual custom template, of course)  
If you don't already have that checkout_success folder at that location, create it. And then copy the tpl_footer.php file from your /includes/templates/YOURTEMPLATE/common/tpl_footer.php ... or if you don't have one there, get it from template_default.  

2\. Using your favorite [text editor](/user/first_steps/useful_tools/#php-html-and-text-editors), save the file, but leave it open in your editor.  

3\. Now, for each parameter that your affiliate company told you needs to be replaced dynamically, substitute the appropriate value from the table below:  

<div class="cms_table">

<table class="cms_table">

<tbody>

<tr valign="top" class="cms_table_tr">

<th width="300" class="cms_table_th">**Value to replace**</th>

<th class="cms_table_th">**What to replace it with**</th>

</tr>

<tr valign="top" class="cms_table_tr">

<td class="cms_table_td">Order Number</td>

<td class="cms_table_td">&lt;?php echo $order_summary['order_number']; ?&gt;</td>

</tr>

<tr valign="top" class="cms_table_tr">

<td class="cms_table_td">Subtotal</td>

<td class="cms_table_td">&lt;?php echo $order_summary['order_subtotal']; ?&gt;</td>

</tr>

<tr valign="top" class="cms_table_tr">

<td class="cms_table_td">Amount of credits/discounts on the order</td>

<td class="cms_table_td">&lt;?php echo $order_summary['credits_applied']; ?&gt;</td>

</tr>

<tr valign="top" class="cms_table_tr">

<td class="cms_table_td">Final Total</td>

<td class="cms_table_td">&lt;?php echo $order_summary['order_total']; ?&gt;</td>

</tr>

<tr valign="top" class="cms_table_tr">

<td class="cms_table_td">Commissionable Order Amount (does not include discounts)</td>

<td class="cms_table_td">&lt;?php echo $order_summary['commissionable_order']; ?&gt;</td>

</tr>

<tr valign="top" class="cms_table_tr">

<td class="cms_table_td">Commissionable amount, formatted with dollar sign and decimal point (per currently selected currency formatting rules set in your admin)</td>

<td class="cms_table_td">&lt;?php echo $order_summary['commissionable_order_formatted']; ?&gt;</td>

</tr>

<tr valign="top" class="cms_table_tr">

<td class="cms_table_td">Coupon Code, if any (often used for referral tracking)</td>

<td class="cms_table_td">&lt;?php echo $order_summary['coupon_code']; ?&gt;</td>

</tr>

<tr valign="top" class="cms_table_tr">

<td class="cms_table_td">Currency Code (3-letter ISO code)</td>

<td class="cms_table_td">&lt;?php echo $order_summary['currency_code']; ?&gt;</td>

</tr>

<tr valign="top" class="cms_table_tr">

<td class="cms_table_td">Exchange Rate applied, if any</td>

<td class="cms_table_td">&lt;?php echo $order_summary['currency_value']; ?&gt;</td>

</tr>

<tr valign="top" class="cms_table_tr">

<td class="cms_table_td">Payment Module used</td>

<td class="cms_table_td">&lt;?php echo $order_summary['payment_module_code']; ?&gt;</td>

</tr>

<tr valign="top" class="cms_table_tr">

<td class="cms_table_td">Shipping Method selected by customer</td>

<td class="cms_table_td">&lt;?php echo $order_summary['shipping_method']; ?&gt;</td>

</tr>

<tr valign="top" class="cms_table_tr">

<td class="cms_table_td">Order Status (number) denoting the order's status in your store at this present time.</td>

<td class="cms_table_td">&lt;?php echo $order_summary['orders_status']; ?&gt;</td>

</tr>

<tr valign="top" class="cms_table_tr">

<td class="cms_table_td">Tax on the order</td>

<td class="cms_table_td">&lt;?php echo $order_summary['tax']; ?&gt;</td>

</tr>

<tr valign="top" class="cms_table_tr">

<td class="cms_table_td">Shipping Cost on the order</td>

<td class="cms_table_td">&lt;?php echo $order_summary['shipping']; ?&gt;</td>

</tr>

<tr valign="top" class="cms_table_tr">

<td class="cms_table_td">Order Total (the final/net total of the order, the amount sent for payment)</td>

<td class="cms_table_td">&lt;?php echo $order_summary['order_total']; ?&gt;</td>

</tr>

<tr valign="top" class="cms_table_tr">

<td class="cms_table_td">Product Model Numbers (delimited with "|")</td>

<td class="cms_table_td">&lt;?php echo $order_summary['products_ordered_models']; ?&gt;</td>

</tr>

<tr valign="top" class="cms_table_tr">

<td class="cms_table_td">Product IDs (delimited with "|")</td>

<td class="cms_table_td">&lt;?php echo $order_summary['products_ordered_ids']; ?&gt;</td>

</tr>

</tbody>

</table>

</div>

Save the file and upload it to your server, keeping in mind the correct folder location as explained in steps 1 and 2.  

4\. Test  

Need to pass details of specific products ordered? See the additional variables outlined in the article linked below.  

Related article: [Integrating Sales Analytics/Affiliate Tools](/user/orders/sales_analytics_affiliate_tools/)
