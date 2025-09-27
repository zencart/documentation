---
title: Configuration ≫ Attribute Settings
category: admin_pages
weight: 110 
---

See also <a href="/user/admin_pages/catalog/attribute_controller/">Admin > Catalog > Attributes Controller</a> for attribute pricing settings.

<h2 id="enable_downloads">Enable Downloads</h2>

<div class='indent'>Key: <b>DOWNLOAD_ENABLED</b><br />
Path: <b>Configuration > Attribute Settings</b><br />
Description: Enable the products download functions.</div>


<h2 id="download_by_redirect">Download by Redirect</h2>

<div class='indent'>Key: <b>DOWNLOAD_BY_REDIRECT</b><br />
Path: <b>Configuration > Attribute Settings</b><br />
Description: Use browser redirection for download. Disable on non-Unix systems.<br /><br />Note: Set /pub to 777 when redirect is true</div>


<h2 id="download_by_streaming">Download by streaming</h2>

<div class='indent'>Key: <b>DOWNLOAD_IN_CHUNKS</b><br />
Path: <b>Configuration > Attribute Settings</b><br />
Description: If download-by-redirect is disabled, and your PHP memory_limit setting is under 8 MB, you might need to enable this setting so that files are streamed in smaller segments to the browser.<br /><br />Has no effect if Download By Redirect is enabled.</div>


<h2 id="download_expiration_number_of_days">Download Expiration (Number of Days)</h2>

<div class='indent'>Key: <b>DOWNLOAD_MAX_DAYS</b><br />
Path: <b>Configuration > Attribute Settings</b><br />
Description: Set number of days before the download link expires. 0 means no limit.</div>


<h2 id="number_of_downloads_allowed__per_product">Number of Downloads Allowed - Per Product</h2>

<div class='indent'>Key: <b>DOWNLOAD_MAX_COUNT</b><br />
Path: <b>Configuration > Attribute Settings</b><br />
Description: Set the maximum number of downloads. 0 means no download authorized.</div>


<h2 id="downloads_controller_update_status_value">Downloads Controller Update Status Value</h2>

<div class='indent'>Key: <b>DOWNLOADS_ORDERS_STATUS_UPDATED_VALUE</b><br />
Path: <b>Configuration > Attribute Settings</b><br />
Description: What orders_status resets the Download days and Max Downloads - Default is 4</div>


<h2 id="downloads_controller_order_status_value_GTE_lower_value">Downloads Controller Order Status Value >= lower value</h2>

<div class='indent'>Key: <b>DOWNLOADS_CONTROLLER_ORDERS_STATUS</b><br />
Path: <b>Configuration > Attribute Settings</b><br />
Description: Downloads Controller Order Status Value - Default >= 2<br /><br />Downloads are available for checkout based on the orders status. Orders with orders status greater than this value will be available for download. The orders status is set for an order by the Payment Modules. Set the lower range for this range.</div>


<h2 id="downloads_controller_order_status_value_LTE_upper_value">Downloads Controller Order Status Value <= upper value</h2>

<div class='indent'>Key: <b>DOWNLOADS_CONTROLLER_ORDERS_STATUS_END</b><br />
Path: <b>Configuration > Attribute Settings</b><br />
Description: Downloads Controller Order Status Value - Default <= 4<br /><br />Downloads are available for checkout based on the orders status. Orders with orders status less than this value will be available for download. The orders status is set for an order by the Payment Modules.  Set the upper range for this range.</div>


<h2 id="enable_price_factor">Enable Price Factor</h2>

<div class='indent'>Key: <b>ATTRIBUTES_ENABLED_PRICE_FACTOR</b><br />
Path: <b>Configuration > Attribute Settings</b><br />
Description: Enable the Attributes Price Factor.</div>


<h2 id="enable_qty_price_discount">Enable Qty Price Discount</h2>

<div class='indent'>Key: <b>ATTRIBUTES_ENABLED_QTY_PRICES</b><br />
Path: <b>Configuration > Attribute Settings</b><br />
Description: Enable the Attributes Quantity Price Discounts.</div>


<h2 id="enable_attribute_images">Enable Attribute Images</h2>

<div class='indent'>Key: <b>ATTRIBUTES_ENABLED_IMAGES</b><br />
Path: <b>Configuration > Attribute Settings</b><br />
Description: Enable the Attributes Images.</div>


<h2 id="enable_text_pricing_by_word_or_letter">Enable Text Pricing by word or letter</h2>

<div class='indent'>Key: <b>ATTRIBUTES_ENABLED_TEXT_PRICES</b><br />
Path: <b>Configuration > Attribute Settings</b><br />
Description: Enable the Attributes Text Pricing by word or letter.</div>


<h2 id="text_pricing__spaces_are_free">Text Pricing - Spaces are Free</h2>

<div class='indent'>Key: <b>TEXT_SPACES_FREE</b><br />
Path: <b>Configuration > Attribute Settings</b><br />
Description: On Text pricing Spaces are Free<br /><br />0= off 1= on</div>


<h2 id="read_only_option_type__ignore_for_add_to_cart">Read Only option type - Ignore for Add to Cart</h2>

<div class='indent'>Key: <b>PRODUCTS_OPTIONS_TYPE_READONLY_IGNORED</b><br />
Path: <b>Configuration > Attribute Settings</b><br />
Description: When a Product only uses READONLY attributes, should the Add to Cart button be On or Off?<br />0= OFF<br />1= ON</div>


