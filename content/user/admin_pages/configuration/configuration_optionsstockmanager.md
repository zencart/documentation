---
title: Configuration ≫ Options' Stock Manager
category: admin_pages
weight: 230 
---

See <a href="/user/running/posm/">Variant Stock</a> for details and instructions on use.

<h2 id="general_enable_products_options_stock_manager">General: Enable Products Options Stock Manager?</h2>

<div class='indent'>Key: <b>POSM_ENABLE</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: Enable the <em>Products' Options' Stock</em> processing for the storefront?</div>


<h2 id="general_duplicate_model_numbers">General: Duplicate Model Numbers</h2>

<div class='indent'>Key: <b>POSM_DUPLICATE_MODELNUMS</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: How should the admin-level tools handle duplicate model numbers?  Choose one of:<ol><li><b>Allow</b> (default): No message, allows saving.</li><li><b>Disallow:</b> Issue message, don't allow saving.</li><li><b>Message-Only:</b> Issue message, allow saving.</li></ol></div>


<h2 id="general_divider_color">General: Divider Color</h2>

<div class='indent'>Key: <b>POSM_DIVIDER_COLOR</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: Enter the background color to be used for the divider in <em>Catalog :: Products' Options' Stock Manager.</em></div>


<h2 id="general_options_stock_reorder_level">General: Options Stock Re-order Level</h2>

<div class='indent'>Key: <b>POSM_STOCK_REORDER_LEVEL</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: Enter the low-stock level for products with options' stock.  This value is used to highlight low-stock options within the <em>Catalog->Manage Options' Stock</em> tools and, if <em>Configuration->E-mail Options->Send Low Stock Emails</em> is enabled, determines the stock-level at which to send those emails.<br><br><strong>Note:</strong> The value entered must consist of numeric (0-9) characters <em>only</em>.</div>


<h2 id="general_backinstock_date_reminder">General: Back-in-Stock Date Reminder</h2>

<div class='indent'>Key: <b>POSM_BIS_DATE_REMINDER</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: If your store is using <em>POSM</em>'s back-in-stock labels with availability dates, you might want a reminder when a date is imminent. Identify the number of days <b>prior to</b> any expiration that the notification should be issued; set the value to 0 (the default) if you do not want a reminder.</div>


<h2 id="general_option_types_to_manage">General: Option Types to Manage?</h2>

<div class='indent'>Key: <b>POSM_OPTIONS_TYPES_TO_MANAGE</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: Enter the types of options to manage using a packed, comma-separated list.  Currently, only Dropdown/Select (0) and Radio (2) option types are supported!</div>


<h2 id="general_optional_emoption_typesem_list">General: Optional <em>Option Types</em> List</h2>

<div class='indent'>Key: <b>POSM_OPTIONAL_OPTION_TYPES_LIST</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: Enter types of options to be ignored when determining if a product's option-combination is managed, using a packed, comma-separated list.<br><br>The built-in Zen Cart option types are Dropdown/Select (0), Text (1), Radio (2), Checkbox (3), File (4) and Read-Only (5).</div>


<h2 id="general_optional_emoption_namesem_list">General: Optional <em>Option Names</em> List</h2>

<div class='indent'>Key: <b>POSM_OPTIONAL_OPTION_NAMES_LIST</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: Enter the list of optional product options for your store, using a packed, comma-separated list of their option_id values. All option  values associated with the options that you identify here are ignored when determining if a product's option-combination is managed.<br><br>Use this value in conjunction with the &quot;Optional <em>Option Types</em> List&quot; to refine your store's option-combination configurations.</div>


<h2 id="stock_status_display_show_messages">Stock Status Display: Show Messages?</h2>

<div class='indent'>Key: <b>POSM_SHOW_STOCK_MESSAGES</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: Choose where (Store Only, Admin Only, Both or Neither) the <em>POSM</em> in-/out-of-stock messages will be displayed.<br><br>If you choose <b>Store Only</b> or <b>Both</b>, this status will be displayed to your customers on the shopping_cart, checkout_confirmation and account_history_info pages. See also the <em>Dependent Attributes: Stock Status Display</em> setting, below, which operates independently of this setting.<br><br>If you choose <b>Admin Only</b> or <b>Both</b>, the in-/out-of-stock messages will be displayed within your <em>Customers-&gt;Orders</em> details display, invoices and packing slips.</div>


<h2 id="stock_status_display__messages_for_unmanaged_options">Stock Status Display:  Messages for Unmanaged Options?</h2>

<div class='indent'>Key: <b>POSM_SHOW_UNMANAGED_OPTIONS_STATUS</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: Should the store-side processing include in-/out-of-stock messages for non-<em>POSM</em>-managed products?  If set to <b>true</b>, the messages will be displayed depending on the unmanaged product's stock quantity &mdash; In Stock if > 0; the default out-of-stock message (PRODUCTS_OPTIONS_STOCK_NOT_IN_STOCK), otherwise.</div>


<h2 id="stock_status_display_include_instock_status">Stock Status Display: Include In-Stock Status?</h2>

<div class='indent'>Key: <b>POSM_SHOW_IN_STOCK_MESSAGE</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: Choose whether to include the display of the &quot;in-stock&quot; product status, <em>wherever</em> that status-display is enabled.  If set to <b>false</b>, only out-of-stock messages will be displayed.</div>


<h2 id="admin_model_number_field_width">Admin: Model Number Field Width</h2>

<div class='indent'>Key: <b>POSM_ADMIN_MODEL_WIDTH</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: Use this setting to control the width of the <em>Option Model/SKU</em> field displayed by <em>Catalog :: Manage Options' Stock</em> and <em>Catalog :: Options' Stock &mdash; View All</em> pages.  Enter a valid CSS &quot;width&quot; value, e.g. 9em (default) or 9px.<br><br><b>Note:</b> Leave the setting blank to use the database-defined field width.<br></div>


<h2 id="dependent_attributes_enable">Dependent Attributes: Enable</h2>

<div class='indent'>Key: <b>POSM_DEPENDENT_ATTRS_ENABLE</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: Identify whether or not the plugin's dependent-attributes processing should be enabled.</div>


<h2 id="dependent_attributes_insert_quotplease_choosequot">Dependent Attributes: Insert &quot;Please Choose&quot;?</h2>

<div class='indent'>Key: <b>POSM_DEPENDENT_ATTRS_PLEASE_CHOOSE</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: Identify whether or not the plugin's dependent-attributes processing should insert a &quot;Please Choose&quot; selection into a product's drop-down options.  If <em>false</em>, the first option value for each attribute is <em>assumed</em> to be a &quot;Please choose &hellip;&quot; type value.<br><br><b>Note:</b> This setting <b><i>does not</i></b> apply when a product has a single drop-down option.</div>


<h2 id="dependent_attributes_show_model_number">Dependent Attributes: Show Model Number?</h2>

<div class='indent'>Key: <b>POSM_DEPENDENT_ATTRS_SHOW_MODEL</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: Identify whether or not the plugin's dependent-attributes processing should include the model-numbers for each attribute value on the final, selectable attribute's option.<br><br><strong>Note:</strong> A model-number is included <b>only if</b> that value is not an empty string.</div>


<h2 id="dependent_attributes_show_stock_status">Dependent Attributes: Show Stock Status?</h2>

<div class='indent'>Key: <b>POSM_DEPENDENT_ATTRS_STOCK_STATUS</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: Identify whether or not the plugin's dependent-attributes processing should include the in-/out-of-stock status for each attribute value on the final, selectable attribute's option.<br><br><strong>Note:</strong> In-stock status is included <em>only</em> if <em>Stock Status Display: Include In-Stock Status?</em> is set to <b>true</b>.</div>


<h2 id="dependent_attributes_show_instock_quantity_in_status">Dependent Attributes: Show In-Stock Quantity in Status?</h2>

<div class='indent'>Key: <b>POSM_DEPENDENT_ATTRS_STOCK_STATUS_QTY</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: When <em>Dependent Attributes: Stock Status Display</em> and <em>Stock Status Display: Include In-Stock Status?</em> are both <b>true</b>, should the in-stock quantity be displayed when the option-combination is <em>In Stock</em>?</div>


<h2 id="dependent_attributes_outer_selector">Dependent Attributes: Outer Selector</h2>

<div class='indent'>Key: <b>POSM_ATTRIBUTE_WRAPPER_SELECTOR</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: Identify the <em>outer</em> CSS selector (default: an empty string) that wraps <b>all</b> elements associated with a single option.<br><br><b>Notes:</b><ol><li>For Zen Cart's built-in <code>responsive_classic</code> and <code>template_default</code> templates (and clones thereof), this value should be set to <em>.attribBlock</em>.</li><li>For the <code>bootstrap</code> template (and clones thereof), this value should be set to an empty string.</li></ul></div>


<h2 id="dependent_attributes_inner_selector">Dependent Attributes: Inner Selector</h2>

<div class='indent'>Key: <b>POSM_ATTRIBUTE_SELECTOR</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: Identify the <em>inner</em> CSS selector (default: <em>.wrapperAttribsOptions</em>) that contains, at a minimum, each option's name. <b>Note:</b> This value should be changed <em>only</em> if your custom template has modified the attributes' display formatting.</div>


<h2 id="dependent_attributes_option_name_selector">Dependent Attributes: Option Name Selector</h2>

<div class='indent'>Key: <b>POSM_OPTION_NAME_SELECTOR</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: Identify the CSS selector (default: <em>.optionName</em>) that identifies the element that contains the current option's name. <b>Note:</b> This value should be changed only if your custom template has modified the attributes' display formatting.</div>


<h2 id="dependent_attributes_attributes_images_selector">Dependent Attributes: Attributes Images Selector</h2>

<div class='indent'>Key: <b>POSM_ATTRIBUTE_IMAGE_SELECTOR</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: Identify the CSS selector (default: <em>.attribImg</em>) that wraps, if configured, each attribute's image. <b>Note:</b> This value should be changed only if your custom template has modified the attributes' display formatting.</div>


<h2 id="dependent_attributes_use_minified_script_file">Dependent Attributes: Use Minified Script File?</h2>

<div class='indent'>Key: <b>POSM_USE_MINIFIED_JSCRIPT</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: Identify whether or not the plugin's dependent-attributes processing should load the minified version of the jQuery script, reducing the page-load time for a product's page.</div>


<h2 id="view_all_allow_model_number_updates">View All: Allow Model Number Updates?</h2>

<div class='indent'>Key: <b>POSM_VIEW_ALL_MODEL_UPDATE</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: Should the &quot;View All&quot; processing for <em>Catalog->Manage Options' Stock</em> enable the managed variants' model numbers to be updated?  If set to <b>false</b>, the model numbers are displayed but cannot be updated; you'll need to update the model numbers on a product-by-product basis.</div>


<h2 id="view_all_maximum_productspage">View All: Maximum Products/Page</h2>

<div class='indent'>Key: <b>POSM_MAX_PRODUCTS_VIEW_ALL</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: Enter the maximum number of products to display on a single page of the <em>View All</em> tool.</div>


<h2 id="shopping_cart_display_model_numbers">Shopping Cart: Display Model Numbers?</h2>

<div class='indent'>Key: <b>POSM_CART_DISPLAY_MODEL_NUMBERS</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: Should the <code>shopping_cart</code> page display a product's model-number?  If you choose <code>true</code>, a product's model number is appended to its name for the display, e.g. &quot;Product Name [model]&quot;, if the model-number is not empty.</div>


<h2 id="enable_debug">Enable debug?</h2>

<div class='indent'>Key: <b>POSM_ENABLE_DEBUG</b><br />
Path: <b>Configuration > Options' Stock Manager</b><br />
Description: If enabled, the <em>POSM</em> processing will write debug information to either a myDEBUG-POSM-*.log (for store-side actions) or a myDEBUG-POSM-adm-*.log (for admin-side actions) file in your store's logs directory.</div>


