---
title: Configuration-Attribute Settings
category: admin_pages
weight: 110
---

<b>Enable Downloads</b>

<div class='indent'>Enable the products download functions.</div>


<b>Download by Redirect</b>

<div class='indent'>Use browser redirection for download. Disable on non-Unix systems.<br /><br />Note: Set /pub to 777 when redirect is true</div>


<b>Download by streaming</b>

<div class='indent'>If download-by-redirect is disabled, and your PHP memory_limit setting is under 8 MB, you might need to enable this setting so that files are streamed in smaller segments to the browser.<br /><br />Has no effect if Download By Redirect is enabled.</div>


<b>Download Expiration (Number of Days)</b>

<div class='indent'>Set number of days before the download link expires. 0 means no limit.</div>


<b>Number of Downloads Allowed - Per Product</b>

<div class='indent'>Set the maximum number of downloads. 0 means no download authorized.</div>


<b>Downloads Controller Update Status Value</b>

<div class='indent'>What orders_status resets the Download days and Max Downloads - Default is 4</div>


<b>Downloads Controller Order Status Value >= lower value</b>

<div class='indent'>Downloads Controller Order Status Value - Default >= 2<br /><br />Downloads are available for checkout based on the orders status. Orders with orders status greater than this value will be available for download. The orders status is set for an order by the Payment Modules. Set the lower range for this range.</div>


<b>Downloads Controller Order Status Value </b>

<div class='indent'>Downloads Controller Order Status Value - Default <= 4<br /><br />Downloads are available for checkout based on the orders status. Orders with orders status less than this value will be available for download. The orders status is set for an order by the Payment Modules.  Set the upper range for this range.</div>


<b>Enable Price Factor</b>

<div class='indent'>Enable the Attributes Price Factor.</div>


<b>Enable Qty Price Discount</b>

<div class='indent'>Enable the Attributes Quantity Price Discounts.</div>


<b>Enable Attribute Images</b>

<div class='indent'>Enable the Attributes Images.</div>


<b>Enable Text Pricing by word or letter</b>

<div class='indent'>Enable the Attributes Text Pricing by word or letter.</div>


<b>Text Pricing - Spaces are Free</b>

<div class='indent'>On Text pricing Spaces are Free<br /><br />0= off 1= on</div>


<b>Read Only option type - Ignore for Add to Cart</b>

<div class='indent'>When a Product only uses READONLY attributes, should the Add to Cart button be On or Off?<br />0= OFF<br />1= ON</div>


