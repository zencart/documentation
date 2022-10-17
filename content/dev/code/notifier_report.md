---
title: Notifier Report 
description: Output of the Zen Cart Notifier Report plugin 
category: code
type: codepage
weight: 10
---

Run on Zen Cart 1.5.8

<!-- RELEASETIME - update -->

<!-- 
To generate this file, run notifier_report.php?markdown on 
an installation of the latest version of Zen Cart.  Get the notifier report
from https://github.com/lat9/notifier_report 
--> 

#### ipn_main_handler.php
```
#328: 'NOTIFY_CHECKOUT_PROCESS_BEFORE_ORDER_TOTALS_PROCESS'
#330: 'NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_TOTALS_PROCESS'
#342: 'NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_CREATE'
#349: 'NOTIFY_CHECKOUT_PROCESS_AFTER_PAYMENT_MODULES_AFTER_ORDER_CREATE'
#376: 'NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_CREATE_ADD_PRODUCTS'
#379: 'NOTIFY_CHECKOUT_PROCESS_AFTER_SEND_ORDER_EMAIL'
#413: 'NOTIFY_CHECKOUT_PROCESS_HANDLE_AFFILIATES', 'paypalipn'
#494: 'NOTIFY_PAYPALIPN_STATUS_HISTORY_UPDATE', array($ordersID, $new_status, $txn_type)

```

#### includes/classes/shopping_cart.php
```
#84: 'NOTIFIER_CART_INSTANTIATE_START'
#86: 'NOTIFIER_CART_INSTANTIATE_END'
#106: 'NOTIFIER_CART_RESTORE_CONTENTS_START'
#190: 'NOTIFIER_CART_RESTORE_CONTENTS_END'
#208: 'NOTIFIER_CART_RESET_START', null, $reset_database
#232: 'NOTIFIER_CART_RESET_END'
#273: 'NOTIFIER_CART_ADD_CART_START', null, $product_id, $qty, $attributes, $notify
#361: 'NOTIFIER_CART_ADD_CART_END', null, $product_id, $qty, $attributes, $notify
#387: 'NOTIFIER_CART_UPDATE_QUANTITY_START', null, $product_id, $quantity, $attributes
#463: 'NOTIFIER_CART_UPDATE_QUANTITY_END'
#479: 'NOTIFIER_CART_CLEANUP_START'
#497: 'NOTIFIER_CART_CLEANUP_END'
#512: 'NOTIFIER_CART_COUNT_CONTENTS_START'
#519: 'NOTIFIER_CART_COUNT_CONTENTS_END'
#534: 'NOTIFIER_CART_GET_QUANTITY_START', null, $product_id
#536: 'NOTIFIER_CART_GET_QUANTITY_END_QTY', null, $product_id
#539: 'NOTIFIER_CART_GET_QUANTITY_END_FALSE', $product_id
#552: 'NOTIFIER_CART_IN_CART_START', null, $product_id
#554: 'NOTIFIER_CART_IN_CART_END_TRUE', null, $product_id
#558: 'NOTIFIER_CART_IN_CART_END_FALSE', $product_id
#571: 'NOTIFIER_CART_REMOVE_START', null, $product_id
#588: 'NOTIFIER_CART_REMOVE_END'
#596: 'NOTIFIER_CART_REMOVE_ALL_START'
#598: 'NOTIFIER_CART_REMOVE_ALL_END'
#657: 'NOTIFY_CART_CALCULATE_PRODUCT_PRICE', $products_id, $product->fields
#736: 'NOTIFY_CART_CALCULATE_ATTRIBUTE_PRICE', $products_id, $attribute_price->fields
#902: 'NOTIFY_CART_CALCULATE_ATTRIBUTE_WEIGHT', ['products_id' => $products_id, 'options_id' => $option], $attribute_weight->fields
#969: 'NOTIFY_CART_ATTRIBUTES_PRICE_START', $product_id
#991: 'NOTIFY_CART_ATTRIBUTES_PRICE_NEXT', $product_id, $attribute_price->fields
#1083: 'NOTIFY_CART_ATTRIBUTES_PRICE_ONETIME_CHARGES_START', $product_id
#1103: 'NOTIFY_CART_ATTRIBUTES_PRICE_ONETIME_CHARGES_NEXT', $product_id, $attribute_price->fields
#1163: 'NOTIFY_CART_ATTRIBUTES_WEIGHT_START', $product_id
#1178: 'NOTIFY_CART_ATTRIBUTES_WEIGHT_NEXT', $product_id, $attribute_weight_info->fields
#1212: 'NOTIFIER_CART_GET_PRODUCTS_START', null, $check_for_valid_cart
#1226: 'NOTIFY_CART_GET_PRODUCTS_NEXT', $products_id, $products->fields
#1390: 'NOTIFIER_CART_GET_PRODUCTS_END', null, $products_array
#1401: 'NOTIFIER_CART_SHOW_TOTAL_START'
#1403: 'NOTIFIER_CART_SHOW_TOTAL_END'
#1414: 'NOTIFIER_CART_SHOW_TOTAL_BEFORE_DISCOUNT_START'
#1416: 'NOTIFIER_CART_SHOW_TOTAL_BEFORE_DISCOUNT_END'
#1869: 'NOTIFIER_CART_OPTIONAL_SUCCESS_UPDATED_CART', $_POST, $goto, $parameters
#2028: 'NOTIFIER_CART_OPTIONAL_SUCCESS_PRODUCT_ADDED_TO_CART', $_POST, $goto, $parameters
#2036: 'NOTIFIER_CART_OPTIONAL_ATTRIBUTE_ERROR_MESSAGE_HOOK', $_POST, $the_list
#2088: 'NOTIFIER_CART_OPTIONAL_SUCCESS_BUYNOW_ADDED_TO_CART', $_GET, $goto, $parameters
#2165: 'NOTIFIER_CART_OPTIONAL_SUCCESS_MULTIPLE_ADDED_TO_CART', $products_list, $goto, $parameters
#2301: 'NOTIFY_CART_USER_ACTION', null, $goto, $parameters

```

#### includes/classes/ViewBuilders/DataTableDataSource.php
```
#23: 'NOTIFY_DATASOURCE_CONSTRUCTOR_END'
#31: 'NOTIFY_DATASOURCE_PROCESSREQUEST', [], $query

```

#### includes/classes/ViewBuilders/BaseController.php
```
#38: 'NOTIFY_TABLEVIEW_PROCESSREQUEST', [], $method

```

#### includes/classes/order.php
```
#149: 'NOTIFY_ORDER_INSTANTIATE', [], $order_id
#167: 'NOTIFY_ORDER_BEFORE_QUERY', [], $order_id
#199: 'NOTIFY_ORDER_COUPON_LINK', $coupon_link->fields, $zc_coupon_link
#366: 'NOTIFY_ORDER_QUERY_ADD_PRODUCT', $this->products[$index], $index
#374: 'NOTIFY_ORDER_AFTER_QUERY', IS_ADMIN_FLAG, $this->orderId
#380: 'ORDER_QUERY_ADMIN_COMPLETE', ['orders_id' => $this->orderId]
#466: 'NOTIFY_ORDER_CART_BEGINS'
#645: 'NOTIFY_ORDER_CART_AFTER_ADDRESSES_SET', '', $taxCountryId, $taxZoneId
#677: 'NOTIFY_ORDER_CART_ADD_PRODUCT_LIST', ['index' => $index, 'products' => $products[$i]]
#714: 'NOTIFY_ORDER_CART_ADD_ATTRIBUTE_LIST', ['index' => $index, 'subindex' => $subindex, 'products' => $products[$i], 'attributes' => $attributes]
#745: 'NOTIFY_ORDER_CART_FINISHED'
#799: 'NOTIFY_ORDER_CART_EXTERNAL_TAX_RATE_LOOKUP', STORE_PRODUCT_TAX_BASIS, $products, $loop, $index, $taxCountryId, $taxZoneId, $taxRates
#826: 'NOTIFY_ORDER_CART_EXTERNAL_TAX_HANDLING', [], $index, $taxCountryId, $taxZoneId
#836: 'NOTIFY_ORDER_CART_SUBTOTAL_CALCULATE', ['shown_price' => $shown_price]
#868: 'NOTIFY_ORDER_CART_EXTERNAL_TAX_DURING_ORDER_CREATE', [], $zf_ot_modules
#879: 'NOTIFY_ORDER_CART_ORDERSTATUS'
#946: 'NOTIFY_ORDER_DURING_CREATE_ADDED_ORDER_HEADER', array_merge(['orders_id' => $this->orderId, 'shipping_weight' => $_SESSION['cart']->weight], $sql_data_array), $this->orderId
#960: 'NOTIFY_ORDER_DURING_CREATE_ADDED_ORDERTOTAL_LINE_ITEM', $sql_data_array, $ot_insert_id
#988: 'NOTIFY_ORDER_DURING_CREATE_ADDED_ORDER_COMMENT', $sql_data_array, $osh_insert_id
#1016: 'NOTIFY_ORDER_PROCESSING_STOCK_DECREMENT_INIT', ['i' => $i], $this->products[$i], $i
#1040: 'NOTIFY_ORDER_PROCESSING_STOCK_DECREMENT_BEGIN', $i, $stock_values
#1067: 'NOTIFY_ORDER_PROCESSING_BESTSELLERS_UPDATE', [], $this->products[$i], $i
#1072: 'NOTIFY_ORDER_PROCESSING_STOCK_DECREMENT_END', $i
#1102: 'NOTIFY_ORDER_DURING_CREATE_ADDED_PRODUCT_LINE_ITEM', array_merge(['orders_products_id' => $order_products_id, 'i' => $i], $sql_data_array), $order_products_id
#1104: 'NOTIFY_ORDER_PROCESSING_CREDIT_ACCOUNT_UPDATE_BEGIN'
#1107: 'NOTIFY_ORDER_PROCESSING_ATTRIBUTES_BEGIN'
#1201: 'NOTIFY_ORDER_DURING_CREATE_ADDED_ATTRIBUTE_LINE_ITEM', array_merge(['orders_products_attributes_id' => $opa_insert_id], $sql_data_array), $opa_insert_id
#1216: 'NOTIFY_ORDER_DURING_CREATE_ADDED_ATTRIBUTE_DOWNLOAD_LINE_ITEM', $sql_data_array, $opd_insert_id
#1222: 'NOTIFY_ORDER_PROCESSING_ATTRIBUTES_EXIST', $attributes_exist
#1224: 'NOTIFY_ORDER_DURING_CREATE_ADD_PRODUCTS', $i, $custom_insertable_text
#1252: 'NOTIFY_ORDER_PROCESSING_ONE_TIME_CHARGES_BEGIN', $i
#1274: 'NOTIFY_ORDER_AFTER_ORDER_CREATE_ADD_PRODUCTS'
#1287: 'NOTIFY_ORDER_SEND_EMAIL_INITIALIZE', [], $zf_insert_id, $order_totals, $zf_mode
#1290: 'NOTIFY_ORDER_SEND_LOW_STOCK_EMAILS'
#1330: 'NOTIFY_ORDER_EMAIL_BEFORE_PRODUCTS', [], $email_order, $html_msg
#1396: 'NOTIFY_ORDER_SET_ORDER_MESSAGE'
#1418: 'NOTIFY_ORDER_INVOICE_CONTENT_READY_TO_SEND', ['zf_insert_id' => $zf_insert_id, 'text_email' => $email_order, 'html_email' => $html_msg], $email_order, $html_msg, $send_customer_email
#1440: 'NOTIFY_ORDER_INVOICE_CONTENT_FOR_ADDITIONAL_EMAILS', $zf_insert_id, $email_order, $html_msg, $sendExtraOrderEmail
#1452: 'NOTIFY_ORDER_AFTER_SEND_ORDER_EMAIL', $zf_insert_id, $email_order, $extra_info, $html_msg

```

#### includes/classes/shipping.php
```
#42: 'NOTIFY_SHIPPING_CLASS_GET_INSTALLED_MODULES', $module
#87: 'NOTIFY_SHIPPING_MODULE_ENABLE', $include_modules[$i]['class'], $include_modules[$i]['class']
#106: 'NOTIFY_SHIPPING_CHECK_ENABLED_FOR_ZONE', [], $class, $enabled
#110: 'NOTIFY_SHIPPING_CHECK_ENABLED', [], $class, $enabled
#119: 'NOTIFY_SHIPPING_MODULE_PRE_CALCULATE_BOXES_AND_TARE', [], $total_weight, $shipping_weight, $shipping_quoted, $shipping_num_boxes
#162: 'NOTIFY_SHIPPING_MODULE_CALCULATE_BOXES_AND_TARE', [], $total_weight, $shipping_weight, $shipping_quoted, $shipping_num_boxes
#210: 'NOTIFY_SHIPPING_MODULE_GET_ALL_QUOTES', $quotes_array, $quotes_array
#254: 'NOTIFY_SHIPPING_EXCLUDE_FROM_CHEAPEST', $rates[$i]['module'], $exclude_from_cheapest
#264: 'NOTIFY_SHIPPING_MODULE_CALCULATE_CHEAPEST', $cheapest, $cheapest, $rates

```

#### includes/classes/payment.php
```
#52: 'NOTIFY_PAYMENT_CLASS_GET_INSTALLED_MODULES', $module
#102: 'NOTIFY_PAYMENT_MODULE_ENABLE'

```

#### includes/classes/Customer.php
```
#78: 'NOTIFY_ZEN_IS_CURRENTLY_LOGGED_IN', null, $is_currently_logged_in
#88: 'NOTIFY_ZEN_IS_LOGGED_IN', null, $is_logged_in
#119: //@TODO        'NOTIFY_?LOGIN_ATTEMPT', null, $is_logged_in
#175: 'NOTIFY_ZEN_IN_GUEST_CHECKOUT', null, $in_guest_checkout
#264: 'NOTIFY_CUSTOMER_DATA_LOADED', $this->data
#350: 'NOTIFY_CUSTOMER_PRICING_GROUP_LOADED', $this->data
#373: 'NOTIFY_CUSTOMER_CHECK_IF_BANNED', $this->data, $banned_status
#382: 'NOTIFY_BAN_CUSTOMER', $this->data, $proceed_with_ban, $reset_shopping_session_and_basket
#699: 'NOTIFY_MODULE_CREATE_ACCOUNT_ADDING_CUSTOMER_RECORD', null, $data
#731: 'NOTIFY_MODULE_CREATE_ACCOUNT_ADDED_CUSTOMER_RECORD', array_merge(['customer_id' => $customer_id], $sql_data_array)
#768: 'NOTIFY_MODULE_CREATE_ACCOUNT_ADDED_ADDRESS_BOOK_RECORD', array_merge(['address_id' => $address_id], $sql_data_array)

```

#### includes/classes/db/mysql/query_factory.php
```
#995: 'NOTIFY_QUERY_FACTORY_META_DEFAULT', ['field' => $field, 'type' => $type], $this->max_length

```

#### includes/classes/QueryBuilder.php
```
#47: 'NOTIFY_QUERYBUILDER_INIT_START'
#63: 'NOTIFY_QUERYBUILDER_INIT_END'
#75: 'NOTIFY_QUERYBUILDER_PROCESSQUERY_START'
#89: 'NOTIFY_QUERYBUILDER_PROCESSQUERY_END'
#94: 'NOTIFY_QUERYBUILDER_SETFINALQUERY_START'
#102: 'NOTIFY_QUERYBUILDER_SETFINALQUERY_END'
#110: 'NOTIFY_QUERYBUILDER_PREPROCESSJOINS_START'
#115: 'NOTIFY_QUERYBUILDER_PREPROCESSJOINS_END'
#124: 'NOTIFY_QUERYBUILDER_PROCESSJOINS_START'
#136: 'NOTIFY_QUERYBUILDER_PROCESSJOINS_END'
#146: 'NOTIFY_QUERYBUILDER_PROCESSJOINSCUSTOMAND_START'
#150: 'NOTIFY_QUERYBUILDER_PROCESSJOINSCUSTOMAND_END'
#160: 'NOTIFY_QUERYBUILDER_PROCESSJOINADDCOLUMN_START'
#168: 'NOTIFY_QUERYBUILDER_PROCESSJOINADDCOLUMN_ENDT'
#178: 'NOTIFY_QUERYBUILDER_PROCESSJOINFKEYFIELD_START'
#195: 'NOTIFY_QUERYBUILDER_PROCESSJOINFKEYFIELD_END'
#203: 'NOTIFY_QUERYBUILDER_PROCESSWHERECLAUSE_START'
#215: 'NOTIFY_QUERYBUILDER_PROCESSWHERECLAUSE_END'
#225: 'NOTIFY_QUERYBUILDER_PROCESSWHERECLAUSETEST_START'
#238: 'NOTIFY_QUERYBUILDER_PROCESSWHERECLAUSETEST_END'
#246: 'NOTIFY_QUERYBUILDER_PROCESSORDERBYS_START'
#261: 'NOTIFY_QUERYBUILDER_PROCESSORDERBYS_END'
#269: 'NOTIFY_QUERYBUILDER_PROCESSGROUPBYS_START'
#284: 'NOTIFY_QUERYBUILDER_PROCESSGROUPBYS_END'
#311: 'NOTIFY_QUERYBUILDER_PROCESSSELECTLIST_START'
#319: 'NOTIFY_QUERYBUILDER_PROCESSSELECTLIST_END'
#327: 'NOTIFY_QUERYBUILDER_PROCESSBINDVARS_START'
#337: 'NOTIFY_QUERYBUILDER_PROCESSBINDVARS_END'
#368: 'NOTIFY_QUERYBUILDER_SETPARTS_START'

```

#### includes/classes/observers/auto.downloads_via_streaming.php
```
#42: 'NOTIFY_DOWNLOAD_WITHOUT_REDIRECT___COMPLETED', $origin_filename
#54: 'NOTIFY_DOWNLOAD_IN_CHUNKS___COMPLETED', $origin_filename
#77: 'NOTIFY_DOWNLOAD_WITHOUT_REDIRECT_VIA_CHUNKS___COMPLETED'

```

#### includes/classes/observers/auto.downloads_via_redirect.php
```
#77: 'NOTIFY_DOWNLOAD_VIA_SYMLINK___BEGINS', array($download_link, $origin_filename, $tempdir)

```

#### includes/init_includes/init_sanitize.php
```
#18: 'NOTIFY_INIT_SANITIZE_STARTS'
#23: 'NOTIFY_INIT_SANITIZE_GET_VAR_CHECK', ['getvarname' => $getvar], $site_array_override
#272: 'NOTIFY_INIT_SANITIZE_ENDS'

```

#### includes/init_includes/init_languages.php
```
#17: 'NOTIFY_LANGUAGE_CHANGE_REQUESTED_BY_VISITOR', $_GET['language'], $lng

```

#### includes/init_includes/init_canonical.php
```
#41: 'NOTIFY_INIT_CANONICAL_PARAM_WHITELIST', $current_page, $excludeParams, $keepableParams, $includeCPath
#112: 'NOTIFY_INIT_CANONICAL_DEFAULT', $current_page, $excludeParams, $canonicalLink
#114: 'NOTIFY_INIT_CANONICAL_FINAL', $current_page, $excludeParams, $canonicalLink

```

#### includes/init_includes/init_customer_auth.php
```
#56: 'NOTIFY_LOGIN_BANNED'

```

#### includes/functions/html_output.php
```
#17: 'NOTIFY_SEFU_INTERCEPT', array(), $link, $page, $parameters, $connection, $add_session_id, $static, $use_dir_ws_catalog
#217: 'NOTIFY_HANDLE_IMAGE', [$newimg]
#225: 'NOTIFY_OPTIMIZE_IMAGE', $template_dir, $src, $title, $width, $height, $parameters
#307: 'PAGE_OUTPUT_IMAGE_SUBMIT'
#331: 'PAGE_OUTPUT_IMAGE_BUTTON'
#363: 'NOTIFY_ZEN_DRAW_BUTTON', null, $text, $classes, $added_classes, $id, $parameters, $title, $type, $the_button
#441:  'NOTIFY_ZEN_CSS_BUTTON_SUBMIT', array( 'button_name' => $button_name, 'text' => $text, 'sec_class' => $sec_class, 'parameters' => $parameters, ), $css_button 
#462:  'NOTIFY_ZEN_CSS_BUTTON_BUTTON', array( 'button_name' => $button_name, 'text' => $text, 'sec_class' => $sec_class, 'parameters' => $parameters, ), $css_button 
#564:  'NOTIFY_ZEN_DRAW_INPUT_FIELD_OVERRIDE', array( 'name' => $name, 'value' => $value, 'parameters' => $parameters, 'type' => $type, 'reinsert_value' => $reinsert_value, 'required' => $required, ), $field 
#594:  'NOTIFY_ZEN_DRAW_INPUT_FIELD', array( 'name' => $name, 'value' => $value, 'parameters' => $parameters, 'type' => $type, 'reinsert_value' => $reinsert_value, 'required' => $required, ), $field 
#629:  'NOTIFY_ZEN_DRAW_SELECTION_FIELD_OVERRIDE', array( 'name' => $name, 'value' => $value, 'parameters' => $parameters, 'type' => $type, 'checked' => $checked ), $selection 
#664:  'NOTIFY_ZEN_DRAW_SELECTION_FIELD', array( 'name' => $name, 'value' => $value, 'parameters' => $parameters, 'type' => $type, 'checked' => $checked ), $selection 
#700:  'NOTIFY_ZEN_DRAW_TEXTAREA_FIELD_OVERRIDE', array( 'name' => $name, 'width' => $width, 'height' => $height, 'text' => $text, 'parameters' => $parameters, 'reinsert_value' => $reinsert_value, ), $field 
#733:  'NOTIFY_ZEN_DRAW_TEXTAREA_FIELD', array( 'name' => $name, 'width' => $width, 'height' => $height, 'text' => $text, 'parameters' => $parameters, 'reinsert_value' => $reinsert_value, ), $field 
#808:  'NOTIFY_ZEN_DRAW_PULL_DOWN_MENU_OVERRIDE', array( 'name' => $name, 'values' => $values, 'default' => $default, 'parameters' => $parameters, 'required' => $required, ), $field 
#857:  'NOTIFY_ZEN_DRAW_PULL_DOWN_MENU', array( 'name' => $name, 'values' => $values, 'default' => $default, 'parameters' => $parameters, 'required' => $required, ), $field 

```

#### includes/functions/functions_categories.php
```
#1062: 'NOTIFIER_ADMIN_ZEN_REMOVE_CATEGORY', array(), $category_id

```

#### includes/functions/functions_products.php
```
#74: 'NOTIFY_PRODUCT_INFO_PRODUCT_STATUS_CHECK', $product_info->fields, $product_status, $should_throw_404, $response_code, $use_custom_response_code
#539:  'ZEN_GET_PRODUCTS_STOCK', $products_id, $products_quantity, $quantity_handled 
#575:  'ZEN_CHECK_STOCK_MESSAGE', [ $products_id, $products_quantity ], $out_of_stock_message 
#781: 'NOTIFY_GET_PRODUCT_ALLOW_ADD_TO_CART', $product_id, $allow_add_to_cart, $product_query_results
#989: 'NOTIFIER_ADMIN_ZEN_REMOVE_PRODUCT', array(), $product_id, $ptc
#1084: 'NOTIFIER_ADMIN_ZEN_PRODUCTS_ATTRIBUTES_DOWNLOAD_DELETE', array(), $product_id

```

#### includes/functions/functions_prices.php
```
#186:  'NOTIFY_ZEN_GET_PRODUCTS_DISPLAY_PRICE_SALE', [ 'products_id' => $product_id, 'display_sale_price' => $display_sale_price, 'display_special_price' => $display_special_price, 'display_normal_price' => $display_normal_price, 'products_tax_class_id' => $product_check->fields['products_tax_class_id'] ], $pricing_handled, $show_sale_discount 
#246:  'NOTIFY_ZEN_GET_PRODUCTS_DISPLAY_PRICE_SPECIAL', [ 'products_id' => $product_id, 'display_sale_price' => $display_sale_price, 'display_special_price' => $display_special_price, 'display_normal_price' => $display_normal_price, 'products_tax_class_id' => $product_check->fields['products_tax_class_id'], 'product_is_free' => $product_check->fields['product_is_free'] ], $pricing_handled, $show_normal_price, $show_special_price, $show_sale_price 
#308:  'NOTIFY_ZEN_GET_PRODUCTS_DISPLAY_PRICE_NORMAL', [ 'products_id' => $product_id, 'display_sale_price' => $display_sale_price, 'display_special_price' => $display_special_price, 'display_normal_price' => $display_normal_price, 'products_tax_class_id' => $product_check->fields['products_tax_class_id'], 'product_is_free' => $product_check->fields['product_is_free'] ], $pricing_handled, $show_normal_price, $show_special_price, $show_sale_price 
#365:  'NOTIFY_ZEN_GET_PRODUCTS_DISPLAY_PRICE_FREE_OR_CALL', [ 'product_is_free' => $product_check->fields['product_is_free'], 'product_is_call' => $product_check->fields['product_is_call'], ], $tags_handled, $free_tag, $call_tag 
#413: 'ZEN_GET_PRODUCTS_BASE_PRICE', $product_id, $products_base_price, $base_price_is_handled

```

#### includes/functions/functions_traffic.php
```
#57: 'NOTIFY_ZEN_ADMIN_INVALID_IP_DETECTED', $original_ip
#59: 'NOTIFY_ZEN_INVALID_IP_DETECTED', $original_ip

```

#### includes/functions/functions_exchange_rates.php
```
#40: 'ADMIN_CURRENCY_EXCHANGE_RATE_MULTIPLIER', $currency->fields['code'], $multiplier, $rate
#51: 'ADMIN_CURRENCY_EXCHANGE_RATE_SINGLE', $currency->fields['code'], $rate
#73: 'ADMIN_CURRENCY_EXCHANGE_RATES_UPDATED', $msg

```

#### includes/functions/functions_osh_update.php
```
#71: 'ZEN_UPDATE_ORDERS_HISTORY_PRE_EMAIL', array('message' => $message), $osh_additional_comments
#89: 'ZEN_UPDATE_ORDERS_HISTORY_STATUS_VALUES', array('orders_id' => $orders_id, 'new' => $orders_new_status, 'old' => $orders_current_status)
#127: 'ZEN_UPDATE_ORDERS_HISTORY_SET_ORDER_UPDATE_MESSAGE', $orders_id, $email_order_message
#195: 'ZEN_UPDATE_ORDERS_HISTORY_BEFORE_INSERT', array(), $osh_sql

```

#### includes/functions/functions_addresses.php
```
#343:  'NOTIFY_END_ZEN_ADDRESS_FORMAT', [ 'format' => $fmt, 'address' => $incoming, 'firstname' => $address['$firstname'], 'lastname' => $address['$lastname'], 'street' => $address['$street'], 'suburb' => $address['$suburb'], 'city' => $address['$city'], 'state' => $address['$state'], 'country' => $address['$country'], 'postcode' => $address['$postcode'], 'company' => $address['$company'], 'streets' => $address['$streets'], 'statecomma' => $address['$statecomma'], 'zip' => $address['$zip'], 'cr' => $address['$cr'], 'hr' => $address['$hr'], ], $address_out 
#392: 'NOTIFY_ZEN_ADDRESS_LABEL', null, $customers_id, $address_id, $address->fields

```

#### includes/functions/functions_customers.php
```
#151: 'NOTIFY_ZEN_IN_GUEST_CHECKOUT', null, $in_guest_checkout
#163: 'NOTIFY_ZEN_IS_LOGGED_IN', null, $is_logged_in

```

#### includes/functions/functions_general.php
```
#211: 'NOTIFY_ZEN_SOLD_OUT_IMAGE', array_merge($button_check->fields, ['products_id' => (int)$product_id]), $return_button
#221: 'NOTIFY_ZEN_GET_BUY_NOW_BUTTON_RETURN', array_merge($button_check->fields, ['products_id' => (int)$product_id]), $return_button

```

#### includes/functions/functions_attributes.php
```
#27: 'NOTIFY_ZEN_HAS_PRODUCT_ATTRIBUTES_CHECK', ['products_id' => $product_id, 'not_readonly' => $not_readonly], $has_attributes
#71: 'NOTIFY_FUNCTIONS_LOOKUPS_REQUIRES_ATTRIBUTES_SELECTION_OTHER', ['products_id' => $products_id], $has_attributes
#94: 'NOTIFY_FUNCTIONS_LOOKUPS_REQUIRES_ATTRIBUTES_SELECTION', '', $query, $noSingles, $noDoubles
#153: 'FUNCTIONS_LOOKUPS_OPTION_NAME_NO_VALUES_OPT_TYPE', $opt_type, $test_var
#175: 'NOTIFY_ZEN_HAS_PRODUCT_ATTRIBUTES_VALUES', $product_id, $value_to_return
#423: 'ZEN_COPY_PRODUCTS_ATTRIBUTES_START', ['from' => (int)$products_id_from, 'to' => (int)$products_id_to]
#435: 'ZEN_COPY_PRODUCTS_ATTRIBUTES_DELETE', (int)$products_id_to
#517: 'ZEN_COPY_PRODUCTS_ATTRIBUTES_ADD', ['pID' => (int)$products_id_to, 'fields' => $copy_from]
#535: 'ZEN_COPY_PRODUCTS_ATTRIBUTES_ADDED_DOWNLOAD', (int)$products_id_to, $new_products_attributes_id, $new_attribute_id
#575: 'ZEN_COPY_PRODUCTS_ATTRIBUTES_UPDATE', ['pID' => (int)$products_id_to, 'fields' => $copy_from]
#580: 'ZEN_COPY_PRODUCTS_ATTRIBUTES_COMPLETE', ['from' => (int)$products_id_from, 'to' => (int)$products_id_to]
#627: 'NOTIFIER_ADMIN_ZEN_DELETE_PRODUCTS_ATTRIBUTES', [], $product_id
#734: 'NOTIFY_TEST_DOWNLOADABLE_FILE_EXISTS', $check_filename, $handler

```

#### includes/functions/functions_taxes.php
```
#23:  'NOTIFY_ZEN_GET_TAX_RATE_OVERRIDE', [ 'class_id' => $class_id, 'country_id' => $country_id, 'zone_id' => $zone_id ], $tax_rate 
#90:  'NOTIFY_ZEN_GET_TAX_DESCRIPTION_OVERRIDE', [ 'class_id' => $class_id, 'country_id' => $country_id, 'zone_id' => $zone_id ], $tax_description 
#155:  'NOTIFY_ZEN_GET_MULTIPLE_TAX_RATES_OVERRIDE', [ 'class_id' => $class_id, 'country_id' => $country_id, 'zone_id' => $zone_id, 'tax_description' => $tax_description ], $rates_array 
#346:  'ZEN_GET_TAX_LOCATIONS', [ 'country' => $store_country, 'zone' => $store_zone ], $tax_address 
#419:  'NOTIFY_ZEN_GET_ALL_TAX_DESCRIPTIONS_OVERRIDE', [ 'country_id' => $country_id, 'zone_id' => $zone_id ], $tax_descriptions 

```

#### includes/functions/functions_email.php
```
#92: 'NOTIFY_EMAIL_ADDRESS_TEST', array(), $to_name, $to_email_address, $email_subject
#95: 'NOTIFY_EMAIL_ADDRESS_VALIDATION_FAILURE', sprintf(EMAIL_SEND_FAILED . ' (failed validation)', $to_name, $to_email_address, $email_subject)
#176: 'NOTIFY_EMAIL_DETERMINING_EMAIL_FORMAT', $to_email_address, $customers_email_format, $module
#196: 'NOTIFY_EMAIL_AFTER_EMAIL_FORMAT_DETERMINED'
#312: 'NOTIFY_EMAIL_BEFORE_PROCESS_ATTACHMENTS', array('attachments'=>$attachments_list, 'module'=>$module), $mail, $attachments_list
#342: 'NOTIFY_EMAIL_AFTER_PROCESS_ATTACHMENTS', sizeof($attachments_list)
#384: 'NOTIFY_EMAIL_READY_TO_SEND', array($mail), $mail
#406: 'NOTIFY_EMAIL_AFTER_SEND'
#411: 'NOTIFY_EMAIL_AFTER_SEND_WITH_ALL_PARAMS', array($to_name, $to_email_address, $from_email_name, $from_email_address, $email_subject, $email_html, $text, $module, $ErrorInfo)
#434: 'NOTIFY_EMAIL_AFTER_SEND_ALL_SPECIFIED_ADDRESSES'
#457: 'NOTIFY_EMAIL_BEGIN_ARCHIVE_WRITE', array($to_name, $to_email_address, $from_email_name, $from_email_address, $email_subject, $email_html, $email_text, $module, $error_msgs)
#760: 'NOTIFY_EMAIL_VALIDATION_TEST', array($email, $valid_address)

```

#### includes/templates/responsive_classic/common/tpl_columnar_display.php
```
#12: 'NOTIFY_TPL_COLUMNAR_DISPLAY_START', $current_page_base, $list_box_contents, $title
#64: <?php 'NOTIFY_TPL_COLUMNAR_DISPLAY_END', $current_page_base, $list_box_contents, $title

```

#### includes/templates/responsive_classic/common/main_template_vars.php
```
#20: 'NOTIFY_MAIN_TEMPLATE_VARS_START', $template_dir
#48: 'NOTIFY_MAIN_TEMPLATE_VARS_END', $template_dir, $body_code

```

#### includes/templates/responsive_classic/common/html_header.php
```
#16: 'NOTIFY_HTML_HEAD_START', $current_page_base, $template_dir
#214: 'NOTIFY_HTML_HEAD_END', $current_page_base

```

#### includes/templates/responsive_classic/common/tpl_main_page.php
```
#266: 'NOTIFY_FOOTER_END', $current_page

```

#### includes/templates/responsive_classic/common/tpl_tabular_display.php
```
#11: 'NOTIFY_TPL_TABULAR_DISPLAY_START', $current_page_base, $list_box_contents
#49: 'NOTIFY_TPL_TABULAR_DISPLAY_END', $current_page_base, $list_box_contents

```

#### includes/templates/template_default/common/tpl_columnar_display.php
```
#12: 'NOTIFY_TPL_COLUMNAR_DISPLAY_START', $current_page_base, $list_box_contents, $title
#65: <?php 'NOTIFY_TPL_COLUMNAR_DISPLAY_END', $current_page_base, $list_box_contents, $title

```

#### includes/templates/template_default/common/main_template_vars.php
```
#20: 'NOTIFY_MAIN_TEMPLATE_VARS_START', $template_dir
#41: 'NOTIFY_MAIN_TEMPLATE_VARS_END', $template_dir, $body_code

```

#### includes/templates/template_default/common/html_header.php
```
#16: 'NOTIFY_HTML_HEAD_START', $current_page_base, $template_dir
#168: 'NOTIFY_HTML_HEAD_END', $current_page_base

```

#### includes/templates/template_default/common/tpl_main_page.php
```
#202: 'NOTIFY_FOOTER_END', $current_page

```

#### includes/templates/template_default/common/tpl_tabular_display.php
```
#11: 'NOTIFY_TPL_TABULAR_DISPLAY_START', $current_page_base, $list_box_contents
#50: 'NOTIFY_TPL_TABULAR_DISPLAY_END', $current_page_base, $list_box_contents

```

#### includes/modules/featured_products.php
```
#67: 'NOTIFY_MODULES_FEATURED_PRODUCTS_B4_LIST_BOX', array(), $featured_products->fields, $products_price

```

#### includes/modules/main_product_image.php
```
#16: 'NOTIFY_MODULES_MAIN_PRODUCT_IMAGE_START'
#38:  'NOTIFY_MODULES_MAIN_PRODUCT_IMAGE_FILENAME', $products_image, $main_image_handled, $products_image_extension, $products_image_base, $products_image_medium, $products_image_large 
#75: 'NOTIFY_MODULES_MAIN_PRODUCT_IMAGE_END'

```

#### includes/modules/specials_index.php
```
#71: 'NOTIFY_MODULES_SPECIALS_INDEX_B4_LIST_BOX', array(), $specials_index->fields, $products_price

```

#### includes/modules/responsive_classic/ezpages_bar_header.php
```
#12: 'NOTIFY_START_EZPAGES_HEADERBAR'
#71: 'NOTIFY_END_EZPAGES_HEADERBAR'

```

#### includes/modules/responsive_classic/product_listing.php
```
#35: 'NOTIFY_MODULE_PRODUCT_LISTING_RESULTCOUNT', $listing_split->number_of_rows
#283: 'NOTIFY_MODULES_PRODUCT_LISTING_PRODUCTS_BUTTON', [], $record, $lc_button
#447: 'NOTIFY_PRODUCT_LISTING_END', $current_page_base, $list_box_contents, $listing_split, $show_top_submit_button, $show_bottom_submit_button, $show_submit, $how_many

```

#### includes/modules/checkout_new_address.php
```
#10: 'NOTIFY_MODULE_START_CHECKOUT_NEW_ADDRESS'
#134: 'NOTIFY_MODULE_CHECKOUT_NEW_ADDRESS_VALIDATION', array(), $error
#160: 'NOTIFY_MODULE_CHECKOUT_ADDED_ADDRESS_BOOK_RECORD', array_merge(array('address_id' => $address_book_id ), $sql_data_array)
#254: 'NOTIFY_MODULE_END_CHECKOUT_NEW_ADDRESS'

```

#### includes/modules/category_row.php
```
#30: 'NOTIFY_CATEGORY_ROW_IMAGE', $next_category['categories_id'], $next_category['categories_image']

```

#### includes/modules/meta_tags.php
```
#15: 'NOTIFY_MODULE_START_META_TAGS', $current_page_base, $metatag_page_name, $meta_tags_over_ride
#34: 'NOTIFY_MODULE_META_TAGS_BUILDKEYWORDS', CUSTOM_KEYWORDS, $keywords_string_metatags
#341: 'NOTIFY_MODULE_META_TAGS_UNSPECIFIEDPAGE', $current_page_base, $metatag_page_name, $meta_tags_over_ride, $metatags_title, $metatags_description, $metatags_keywords
#349: 'NOTIFY_MODULE_META_TAGS_OVERRIDE', $metatag_page_name, $meta_tags_over_ride, $metatags_title, $metatags_description, $metatags_keywords
#359: 'NOTIFY_MODULE_END_META_TAGS'

```

#### includes/modules/attributes.php
```
#117: 'NOTIFY_ATTRIBUTES_MODULE_START_OPTION', $products_options_names->fields
#146: 'NOTIFY_ATTRIBUTES_MODULE_START_OPTIONS_LOOP', $i++, $products_options->fields, $products_options_names->fields, $data_properties, $field_disabled, $attributeDetailsArrayForJson
#202: 'NOTIFY_ATTRIBUTES_MODULE_SALEMAKER_DISPLAY_PRICE_PERCENTAGE', $products_options->fields, $product_info->fields, $products_options_display_price, $data_properties
#222: 'NOTIFY_ATTRIBUTES_MODULE_ORIGINAL_PRICE', $products_options->fields, $products_options_array, $products_options_display_price, $data_properties
#295: 'NOTIFY_ATTRIBUTES_MODULE_RADIO_SELECTED', $products_options->fields, $data_properties
#384: 'NOTIFY_ATTRIBUTES_MODULE_CHECKBOX_SELECTED', $products_options->fields, $data_properties
#520: 'NOTIFY_ATTRIBUTES_MODULE_FORMAT_VALUE', array_merge($products_options->fields, $products_options_names->fields), $data_properties, $field_disabled, $attributeDetailsArrayForJson
#559: 'NOTIFY_ATTRIBUTES_MODULE_BEFORE_ASSEMBLE_OUTPUTS', $products_options->fields, $data_properties, $inputFieldId, $field_disabled
#635: 'NOTIFY_ATTRIBUTES_MODULE_DEFAULT_SWITCH', $products_options_names->fields, $options_name, $options_menu, $options_comment, $options_comment_position, $options_html_id, $data_properties, $options_inputfield_id
#642: 'NOTIFY_ATTRIBUTES_MODULE_OPTION_BUILT', $products_options_names->fields, $options_name, $options_menu, $options_comment, $options_comment_position, $options_html_id, $options_attributes_image, $data_properties, $options_inputfield_id
#647: 'NOTIFY_ATTRIBUTES_MODULE_END', $prod_id, $options_name, $options_menu, $options_comment, $options_comment_position, $options_html_id, $options_attributes_image, $options_inputfield_id, $attributeDetailsArrayForJson

```

#### includes/modules/create_account.php
```
#10: 'NOTIFY_MODULE_START_CREATE_ACCOUNT'
#41: 'NOTIFY_CREATE_ACCOUNT_CAPTCHA_CHECK', $antiSpamFieldName, $antiSpam
#152: 'NOTIFY_CREATE_ACCOUNT_LOOKUP_BY_EMAIL', $email_address, $already_exists, $send_welcome_email
#159: 'NOTIFY_NICK_CHECK_FOR_EXISTING_EMAIL', $email_address, $nick_error, $nick
#167: 'NOTIFY_NICK_CHECK_FOR_MIN_LENGTH', $nick, $nick_error, $nick_length_min
#169: 'NOTIFY_NICK_CHECK_FOR_DUPLICATE', $nick, $nick_error
#258: 'NOTIFY_CREATE_ACCOUNT_VALIDATION_CHECK', array(), $error, $send_welcome_email
#270: 'NOTIFY_FAILURE_DURING_CREATE_ACCOUNT'
#272: 'NOTIFY_SPAM_DETECTED_DURING_CREATE_ACCOUNT'
#298: 'NOTIFY_NICK_CREATE_NEW', $nick, $password, $nick_email, $extra_welcome_text
#301: 'NOTIFY_LOGIN_SUCCESS_VIA_CREATE_ACCOUNT', $email_address, $extra_welcome_text, $send_welcome_email
#406: 'NOTIFY_NICK_SET_TEMPLATE_FLAG', 0, $display_nick_field
#410: 'NOTIFY_MODULE_END_CREATE_ACCOUNT'

```

#### includes/modules/payment/authorizenet.php
```
#354: 'NOTIFY_PAYMENT_AUTHNETSIM_PRESUBMIT_HOOK'
#427: 'NOTIFY_PAYMENT_AUTHNETSIM_POSTSUBMIT_HOOK', $this->authorize
#466: 'NOTIFY_PAYMENT_AUTHNETSIM_POSTPROCESS_HOOK'

```

#### includes/modules/payment/paypaldp.php
```
#1226: 'NOTIFY_PAYMENT_PAYPALDP_INSTALLED'
#1246: 'NOTIFY_PAYMENT_PAYPALDP_UNINSTALLED'
#1631: 'NOTIFY_PAYMENT_PAYPALDP_SUBTOTALS_REVIEW', $order, $order_totals

```

#### includes/modules/payment/paypalwpp.php
```
#465: 'NOTIFY_PAYPALWPP_BEFORE_DOEXPRESSCHECKOUT'
#522: 'NOTIFY_PAYPALWPP_BEFORE_PROCESS_FINISHED', $response
#590: 'NOTIFY_PAYPALWPP_AFTER_PROCESS_FINISHED', $paypal_order
#745: 'NOTIFY_PAYMENT_PAYPALWPP_INSTALLED'
#788: 'NOTIFY_PAYMENT_PAYPALWPP_UNINSTALLED'
#1324: 'NOTIFY_PAYMENT_PAYPALEC_SUBTOTALS_TAX', $order, $order_totals
#1417: 'NOTIFY_PAYPALWPP_GETLINEITEMDETAILS', $numberOfLineItemsProcessed, $optionsLI
#1767: 'NOTIFY_PAYMENT_PAYPALEC_BEFORE_SETEC', array(), $options, $order, $order_totals
#1775: 'NOTIFY_PAYMENT_PAYPALEC_TOKEN', $response, $options
#1892: 'NOTIFY_PAYPALEC_PARSE_GETEC_RESULT', array(), $response
#1930: 'NOTIFY_PAYPAL_EXPRESS_CHECKOUT_PAYERID_DETERMINED', $response['PAYERID']
#2066: 'NOTIFY_PAYPAL_CUSTOMER_ATTEMPT_TO_USE_INVALID_COUNTRY_CODE'
#2162: 'NOTIFY_PAYPALEXPRESS_BYPASS_ADDRESS_CREATION', $paypal_ec_payer_info, $bypass_address_creation
#2272: 'NOTIFY_PAYPALEXPRESS_CREATE_ACCOUNT_ADDED_CUSTOMER_RECORD', $customer_id, $sql_data_array
#2303: 'NOTIFY_PAYPALEXPRESS_CREATE_ACCOUNT_ADDED_ADDRESS_BOOK_RECORD', array(), $address_id, $sql_data_array
#2356: 'NOTIFY_LOGIN_SUCCESS_VIA_CREATE_ACCOUNT', 'paypal express checkout'
#2397: 'NOTIFY_PAYPALEC_END_ECSTEP2', $order
#2469: 'NOTIFY_PAYPALWPP_DISABLE_GET_OVERRIDE_ADDRESS', $address_id, $disable_address_override
#2728: 'NOTIFY_HEADER_ADDRESS_BOOK_ADD_ENTRY_INVALID_ATTEMPT', $customer_id, $country_id, $address_format_id, $address_question_arr
#2799: 'NOTIFY_HEADER_ADDRESS_BOOK_ADD_ENTRY_DONE', 'paypal express checkout', $new_address_book_id, $sql_data_array, $make_default
#3086: 'NOTIFY_PAYPALWPP_ERROR_HANDLER', $response, $operation, $basicError, $ignoreList, $errorInfo

```

#### includes/modules/payment/firstdata_hco.php
```
#314: 'MODULE_PAYMENT_FIRSTDATA_PAYMENTPAGES_PRESUBMIT_HOOK'
#367: 'MODULE_PAYMENT_FIRSTDATA_PAYMENTPAGES_POSTSUBMIT_HOOK', $this->authorize
#401: 'MODULE_PAYMENT_FIRSTDATA_PAYMENTPAGES_POSTPROCESS_HOOK'

```

#### includes/modules/payment/paypal/paypal_curl.php
```
#113: 'NOTIFY_PAYPAL_CURL_CONSTRUCT', $params
#160: 'NOTIFY_PAYPAL_SETEXPRESSCHECKOUT'
#176: 'NOTIFY_PAYPAL_GETEXPRESSCHECKOUTDETAILS'
#200: 'NOTIFY_PAYPAL_DOEXPRESSCHECKOUTPAYMENT'
#243: 'NOTIFY_PAYPAL_DODIRECTPAYMENT'
#565: 'NOTIFY_PAYPAL_CURL_BUILDNAMEVALUELIST', $string
#666: 'PAYPAL_CURL_LOG', $token, $tokenHash

```

#### includes/modules/payment/authorizenet_aim.php
```
#416: 'NOTIFY_PAYMENT_AUTHNET_EMULATOR_CHECK', $this->code, $submit_data
#431: 'NOTIFY_PAYMENT_AUTHNET_PRESUBMIT_HOOK', $this->code, $submit_data
#437: 'NOTIFY_PAYMENT_AUTHNET_POSTSUBMIT_HOOK', $this->code, $response
#621: 'NOTIFY_PAYMENT_AUTHNET_MODE_SELECTION', $this->mode, $submit_data
#701: 'NOTIFY_PAYMENT_AUTHNET_ENCAPSULATION_CHECK'

```

#### includes/modules/payment/paypal.php
```
#405: 'NOTIFY_PAYMENT_PAYPAL_RETURN_TO_STORE', $_GET
#430: 'NOTIFY_PAYMENT_PAYPAL_CANCELLED_DURING_CHECKOUT', $_GET
#581: 'NOTIFY_PAYMENT_PAYPAL_INSTALLED'
#590: 'NOTIFY_PAYMENT_PAYPAL_UNINSTALLED'

```

#### includes/modules/downloads.php
```
#107: 'NOTIFY_MODULE_DOWNLOAD_TEMPLATE_DETAILS', $data, $data

```

#### includes/modules/product_listing_alpha_sorter.php
```
#28: 'NOTIFY_PRODUCT_LISTING_ALPHA_SORTER_SELECTLIST', isset($prefix) ? $prefix : '', $letters_list

```

#### includes/modules/additional_images.php
```
#14: 'NOTIFY_MODULES_ADDITIONAL_PRODUCT_IMAGES_START'
#54:  'NOTIFY_MODULES_ADDITIONAL_IMAGES_FILE_MATCH', array( 'file' => $file, 'file_extension' => $file_extension, 'products_image' => $products_image, 'products_image_base' => $products_image_base ), $current_image_match 
#85: 'NOTIFY_MODULES_ADDITIONAL_PRODUCT_IMAGES_LIST', NULL, $images_array
#112: 'NOTIFY_MODULES_ADDITIONAL_IMAGES_GET_LARGE', $products_name, $products_image_large
#127: 'NOTIFY_MODULES_ADDITIONAL_IMAGES_THUMB_SLASHES', array(), $thumb_slashes
#146:  'NOTIFY_MODULES_ADDITIONAL_IMAGES_SCRIPT_LINK', array( 'flag_display_large' => $flag_display_large, 'products_name' => $products_name, 'products_image_large' => $products_image_large, 'thumb_slashes' => $thumb_slashes, 'large_link' => $large_link, 'index' => $i ), $script_link, $link_parameters 
#183: 'NOTIFY_MODULES_ADDITIONAL_PRODUCT_IMAGES_END'

```

#### includes/modules/checkout_address_book.php
```
#18: 'NOTIFY_MODULE_END_CHECKOUT_ADDRESS_BOOK', $customer, $addresses

```

#### includes/modules/sideboxes/ezpages.php
```
#10: 'NOTIFY_START_EZPAGES_SIDEBOX'
#71: 'NOTIFY_END_EZPAGES_SIDEBOX'
#76: 'NOTIFY_END_EZPAGES_SIDEBOX'

```

#### includes/modules/ezpages_bar_header.php
```
#12: 'NOTIFY_START_EZPAGES_HEADERBAR'
#71: 'NOTIFY_END_EZPAGES_HEADERBAR'

```

#### includes/modules/checkout_process.php
```
#12: 'NOTIFY_CHECKOUT_PROCESS_BEGIN'
#31: 'NOTIFY_CHECKOUT_SLAMMING_ALERT', $_SESSION['payment_attempt'], $slamming_threshold
#33: 'NOTIFY_CHECKOUT_SLAMMING_LOCKOUT'
#73: 'NOTIFY_CHECKOUT_PROCESS_BEFORE_ORDER_TOTALS_PRE_CONFIRMATION_CHECK'
#88: 'NOTIFY_CHECKOUT_PROCESS_BEFORE_ORDER_TOTALS_PROCESS'
#90: 'NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_TOTALS_PROCESS'
#98: 'NOTIFY_CHECKOUT_PROCESS_AFTER_PAYMENT_MODULES_BEFOREPROCESS'
#101: 'NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_CREATE', $insert_id
#103: 'NOTIFY_CHECKOUT_PROCESS_AFTER_PAYMENT_MODULES_AFTER_ORDER_CREATE', $insert_id
#107: 'NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_CREATE_ADD_PRODUCTS', $insert_id, $order
#110: 'NOTIFY_CHECKOUT_PROCESS_AFTER_SEND_ORDER_EMAIL', $insert_id, $order
#150: 'NOTIFY_CHECKOUT_PROCESS_HANDLE_AFFILIATES'

```

#### includes/modules/ezpages_bar_footer.php
```
#12: 'NOTIFY_START_EZPAGES_FOOTERBAR'
#70: 'NOTIFY_END_EZPAGES_FOOTERBAR'

```

#### includes/modules/product_listing.php
```
#35: 'NOTIFY_MODULE_PRODUCT_LISTING_RESULTCOUNT', $listing_split->number_of_rows
#273: 'NOTIFY_MODULES_PRODUCT_LISTING_PRODUCTS_BUTTON', [], $record, $lc_button
#426: 'NOTIFY_PRODUCT_LISTING_END', $current_page_base, $list_box_contents, $listing_split, $show_top_submit_button, $show_bottom_submit_button, $show_submit, $how_many

```

#### includes/modules/order_total/ot_shipping.php
```
#96:  'NOTIFY_OT_SHIPPING_TAX_CALCS', array(), $external_shipping_tax_handler, $shipping_tax, $shipping_tax_description 

```

#### includes/modules/order_total/ot_coupon.php
```
#252: 'NOTIFY_OT_COUPON_GENERATE_POPUP_LINK', ['coupon_id' => $coupon_id, 'coupon_code' => $coupon_code], $couponLink
#356: 'NOTIFY_OT_COUPON_COUPON_INFO', ['coupon_result' => $coupon_details, 'code' => $coupon_code]
#609: 'NOTIFY_OT_COUPON_CALCS_FINISHED', ['coupon' => $coupon_details, 'order_totals' => $orderTotalDetails, 'od_amount' => $od_amount], $coupon_details
#638: 'NOTIFY_OT_COUPON_PRODUCT_VALIDITY', ['is_product_valid' => $is_product_valid, 'i' => $i]
#773: 'NOTIFY_OT_COUPON_COUPON_REMOVED'
#807: 'NOTIFY_COUPON_VALIDATION_PRODUCT_RESTRICTIONS', $coupon_id, $products, $found_valid
#985: 'NOTIFY_OT_COUPON_USES_PER_USER_CHECK', $coupon_details, $valid
#1006: 'NOTIFY_OT_COUPON_USES_PER_CUSTOMER_GUEST_CHECKOUT_CHECK', $coupon_details, $valid

```

#### includes/modules/new_products.php
```
#80: 'NOTIFY_MODULES_NEW_PRODUCTS_B4_LIST_BOX', [], $new_products->fields, $products_price

```

#### includes/modules/pages/page/header_php.php
```
#18: 'NOTIFY_HEADER_START_EZPAGE'
#194: 'NOTIFY_HEADER_END_EZPAGE'

```

#### includes/modules/pages/checkout_success/header_php.php
```
#11: 'NOTIFY_HEADER_START_CHECKOUT_SUCCESS'
#171: 'NOTIFY_HEADER_END_CHECKOUT_SUCCESS'

```

#### includes/modules/pages/create_account_success/header_php.php
```
#11: 'NOTIFY_HEADER_START_CREATE_ACCOUNT_SUCCESS'
#64: 'NOTIFY_HEADER_END_CREATE_ACCOUNT_SUCCESS'

```

#### includes/modules/pages/account_history_info/header_php.php
```
#10: 'NOTIFY_HEADER_START_ACCOUNT_HISTORY_INFO'
#36: 'NOTIFY_HEADER_END_ACCOUNT_HISTORY_INFO'

```

#### includes/modules/pages/product_free_shipping_info/main_template_vars.php
```
#14: 'NOTIFY_MAIN_TEMPLATE_VARS_START_PRODUCT_FREE_SHIPPING_INFO'
#34: 'NOTIFY_PRODUCT_VIEWS_HIT_INCREMENTOR', (int)$_GET['products_id']
#109: 'NOTIFY_MAIN_TEMPLATE_VARS_PRODUCT_TYPE_VARS_PRODUCT_FREE_SHIPPING_INFO'
#149: 'NOTIFY_MAIN_TEMPLATE_VARS_EXTRA_PRODUCT_FREE_SHIPPING_INFO'
#157: 'NOTIFY_MAIN_TEMPLATE_VARS_END_PRODUCT_FREE_SHIPPING_INFO'

```

#### includes/modules/pages/product_free_shipping_info/header_php.php
```
#11: 'NOTIFY_HEADER_START_PRODUCT_FREE_SHIPPING_INFO'
#25: 'NOTIFY_HEADER_END_PRODUCT_FREE_SHIPPING_INFO'

```

#### includes/modules/pages/product_free_shipping_info/main_template_vars_product_type.php
```
#17: 'NOTIFY_PRODUCT_TYPE_VARS_START_PRODUCT_FREE_SHIPPING_INFO'
#35: 'NOTIFY_PRODUCT_TYPE_VARS_END_PRODUCT_FREE_SHIPPING_INFO'

```

#### includes/modules/pages/account_history/header_php.php
```
#10: 'NOTIFY_HEADER_START_ACCOUNT_HISTORY'
#28: 'NOTIFY_HEADER_END_ACCOUNT_HISTORY'

```

#### includes/modules/pages/checkout_payment/header_php.php
```
#11: 'NOTIFY_HEADER_START_CHECKOUT_PAYMENT'
#122: 'NOTIFY_HEADER_END_CHECKOUT_PAYMENT'

```

#### includes/modules/pages/document_general_info/main_template_vars.php
```
#14: 'NOTIFY_MAIN_TEMPLATE_VARS_START_DOCUMENT_GENERAL_INFO'
#34: 'NOTIFY_PRODUCT_VIEWS_HIT_INCREMENTOR', (int)$_GET['products_id']
#109: 'NOTIFY_MAIN_TEMPLATE_VARS_PRODUCT_TYPE_VARS_DOCUMENT_GENERAL_INFO'
#150: 'NOTIFY_MAIN_TEMPLATE_VARS_EXTRA_DOCUMENT_GENERAL_INFO'
#158: 'NOTIFY_MAIN_TEMPLATE_VARS_END_DOCUMENT_GENERAL_INFO'

```

#### includes/modules/pages/document_general_info/header_php.php
```
#11: 'NOTIFY_HEADER_START_DOCUMENT_GENERAL_INFO'
#20: 'NOTIFY_HEADER_END_DOCUMENT_GENERAL_INFO'

```

#### includes/modules/pages/document_general_info/main_template_vars_product_type.php
```
#17: 'NOTIFY_PRODUCT_TYPE_VARS_START_DOCUMENT_GENERAL_INFO'
#35: 'NOTIFY_PRODUCT_TYPE_VARS_END_DOCUMENT_GENERAL_INFO'

```

#### includes/modules/pages/checkout_confirmation/header_php.php
```
#11: 'NOTIFY_HEADER_START_CHECKOUT_CONFIRMATION'
#171: 'NOTIFY_HEADER_END_CHECKOUT_CONFIRMATION'

```

#### includes/modules/pages/product_reviews/header_php.php
```
#11: 'NOTIFY_HEADER_START_PRODUCT_REVIEWS'
#86: 'NOTIFY_HEADER_END_PRODUCT_REVIEWS'

```

#### includes/modules/pages/search_result/header_php.php
```
#11: 'NOTIFY_HEADER_START_ADVANCED_SEARCH_RESULTS'
#33: 'NOTIFY_ADVANCED_SEARCH_RESULTS_ADDL_CLAUSE', [], $search_additional_clause
#210: 'NOTIFY_SEARCH_COLUMNLIST_STRING'
#224: 'NOTIFY_SEARCH_SELECT_STRING'
#256: 'NOTIFY_SEARCH_FROM_STRING'
#385: 'NOTIFY_SEARCH_WHERE_STRING'
#447: 'NOTIFY_SEARCH_ORDERBY_STRING', $listing_sql
#454: 'NOTIFY_SEARCH_RESULTS', $listing_sql, $keywords, $result
#466: 'NOTIFY_HEADER_END_ADVANCED_SEARCH_RESULTS', $keywords

```

#### includes/modules/pages/brands/header_php.php
```
#10: 'NOTIFY_HEADER_START_BRANDS'
#55: 'NOTIFY_HEADER_END_BRANDS'

```

#### includes/modules/pages/contact_us/header_php.php
```
#11: 'NOTIFY_HEADER_START_CONTACT_US'
#30: 'NOTIFY_CONTACT_US_CAPTCHA_CHECK', $_POST
#37: 'NOTIFY_SPAM_DETECTED_USING_CONTACT_US', $_POST
#57: 'NOTIFY_CONTACT_US_ACTION', $_SESSION['customer_id'] ?? 0, $customer_email, $customer_name, $email_address, $name, $enquiry, $telephone
#157: 'NOTIFY_HEADER_END_CONTACT_US'

```

#### includes/modules/pages/featured_products/header_php.php
```
#11: 'NOTIFY_HEADER_START_FEATURED_PRODUCTS'
#36: 'NOTIFY_FEATURED_PRODUCTS_SQL_STRING', array(), $featured_products_query_raw, $count_key
#82: 'NOTIFY_HEADER_END_FEATURED_PRODUCTS', $how_many

```

#### includes/modules/pages/gv_send/header_php.php
```
#14: 'NOTIFY_HEADER_START_GV_SEND'
#214: 'NOTIFY_HEADER_END_GV_SEND'

```

#### includes/modules/pages/specials/main_template_vars.php
```
#24: 'NOTIFY_SPECIALS_MAIN_TEMPLATE_VARS_SQL_STRING', array(), $specials_query_raw, $count_key
#56: 'NOTIFY_SPECIALS_MAIN_TEMPLATE_VARS_END', array(), $list_box_contents

```

#### includes/modules/pages/specials/header_php.php
```
#9: 'NOTIFY_HEADER_START_SPECIALS'

```

#### includes/modules/pages/checkout_shipping/header_php.php
```
#10: 'NOTIFY_HEADER_START_CHECKOUT_SHIPPING'
#230: 'NOTIFY_HEADER_END_CHECKOUT_SHIPPING'

```

#### includes/modules/pages/ask_a_question/header_php.php
```
#9: 'NOTIFY_HEADER_START_ASK_A_QUESTION'
#53: 'NOTIFY_ASK_A_QUESTION_CAPTCHA_CHECK', $_POST
#60: 'NOTIFY_SPAM_DETECTED_USING_CONTACT_US', $_POST
#80: 'NOTIFY_ASK_A_QUESTION_ACTION', (isset($_SESSION['customer_id']) ? $_SESSION['customer_id'] : 0), $customer_email, $customer_name, $email_address, $name, $enquiry, $telephone
#174: 'NOTIFY_HEADER_END_ASK_A_QUESTION'

```

#### includes/modules/pages/page_not_found/header_php.php
```
#11: 'NOTIFY_HEADER_START_PAGE_NOT_FOUND'
#27: 'NOTIFY_HEADER_END_PAGE_NOT_FOUND'

```

#### includes/modules/pages/password_forgotten/header_php.php
```
#11: 'NOTIFY_HEADER_START_PASSWORD_FORGOTTEN'
#44: 'NOTIFY_PASSWORD_FORGOTTEN_VALIDATED', $email_address, $sessionMessage
#66: 'NOTIFY_PASSWORD_FORGOTTEN_CHANGED', $email_address, $check_customer->fields['customers_id'], $new_password
#69: 'NOTIFY_PASSWORD_FORGOTTEN_NOT_FOUND', $email_address, $sessionMessage
#81: 'NOTIFY_HEADER_END_PASSWORD_FORGOTTEN'

```

#### includes/modules/pages/unsubscribe/header_php.php
```
#11: 'NOTIFY_HEADER_START_UNSUBSCRIBE'
#56: 'NOTIFY_HEADER_END_UNSUBSCRIBE'

```

#### includes/modules/pages/order_status/header_php.php
```
#8: 'NOTIFY_HEADER_START_ORDER_STATUS'
#25: 'NOTIFY_HEADER_END_ORDER_STATUS'

```

#### includes/modules/pages/account_newsletters/header_php.php
```
#10: 'NOTIFY_HEADER_START_ACCOUNT_NEWSLETTERS'
#45: 'NOTIFY_HEADER_ACCOUNT_NEWSLETTER_UPDATED', $newsletter_general
#56: 'NOTIFY_HEADER_END_ACCOUNT_NEWSLETTERS'

```

#### includes/modules/pages/popup_image_additional/header_php.php
```
#10: 'NOTIFY_HEADER_START_POPUP_IMAGES_ADDITIONAL'
#49: 'NOTIFY_HEADER_END_POPUP_IMAGES_ADDITIONAL'

```

#### includes/modules/pages/document_product_info/main_template_vars.php
```
#14: 'NOTIFY_MAIN_TEMPLATE_VARS_START_DOCUMENT_PRODUCT_INFO'
#34: 'NOTIFY_PRODUCT_VIEWS_HIT_INCREMENTOR', (int)$_GET['products_id']
#109: 'NOTIFY_MAIN_TEMPLATE_VARS_PRODUCT_TYPE_VARS_DOCUMENT_PRODUCT_INFO'
#149: 'NOTIFY_MAIN_TEMPLATE_VARS_EXTRA_DOCUMENT_PRODUCT_INFO'
#157: 'NOTIFY_MAIN_TEMPLATE_VARS_END_DOCUMENT_PRODUCT_INFO'

```

#### includes/modules/pages/document_product_info/header_php.php
```
#11: 'NOTIFY_HEADER_START_DOCUMENT_PRODUCT_INFO'
#25: 'NOTIFY_HEADER_END_DOCUMENT_PRODUCT_INFO'

```

#### includes/modules/pages/document_product_info/main_template_vars_product_type.php
```
#17: 'NOTIFY_PRODUCT_TYPE_VARS_START_DOCUMENT_PRODUCT_INFO'
#35: 'NOTIFY_PRODUCT_TYPE_VARS_END_DOCUMENT_PRODUCT_INFO'

```

#### includes/modules/pages/gv_redeem/header_php.php
```
#9: 'NOTIFY_HEADER_START_GV_REDEEM'

```

#### includes/modules/pages/popup_image/header_php.php
```
#14: 'NOTIFY_HEADER_START_POPUP_IMAGES'
#63: 'NOTIFY_HEADER_END_POPUP_IMAGES'

```

#### includes/modules/pages/time_out/header_php.php
```
#11: 'NOTIFY_HEADER_START_LOGIN_TIMEOUT'
#18: 'NOTIFY_HEADER_END_LOGIN_TIMEOUT'

```

#### includes/modules/pages/download/header_php.php
```
#14: 'NOTIFY_HEADER_START_DOWNLOAD'
#54: 'NOTIFY_DOWNLOAD_NO_MATCH_FOUND', $sql
#88: 'NOTIFY_CHECK_DOWNLOAD_HANDLER', $downloads, $downloads->fields, $origin_filename, $browser_filename, $source_directory, $file_exists, $service, $isExpired, $download_timestamp
#140: 'NOTIFY_DOWNLOAD_BROWSER_DETECTION', array(), $detectedBrowser, $_SERVER['HTTP_USER_AGENT'], $version, $browser_headers_override, $browser_extra_headers
#146: 'NOTIFY_DOWNLOAD_BEFORE_START', $_SESSION['customers_host_address'], $service, $origin_filename, $browser_filename, $source_directory, $downloadFilesize, $mime_type, $downloads->fields, $browser_headers_override
#147: 'NOTIFY_DOWNLOAD_READY_TO_START', $_SESSION['customers_host_address'], $service, $origin_filename, $browser_filename, $source_directory, $downloadFilesize, $mime_type, $downloads->fields, $browser_headers_override
#210: 'NOTIFY_DOWNLOAD_READY_TO_REDIRECT', array(), $service, $origin_filename, $browser_filename, $source_directory, $link_create_status
#214: 'NOTIFY_DOWNLOAD_READY_TO_STREAM', array(), $service, $origin_filename, $browser_filename, $source_directory, $downloadFilesize
#216: 'NOTIFY_HEADER_END_DOWNLOAD'

```

#### includes/modules/pages/checkout_payment_address/header_php.php
```
#11: 'NOTIFY_HEADER_START_CHECKOUT_PAYMENT_ADDRESS'
#44: 'NOTIFY_HEADER_END_CHECKOUT_PAYMENT_ADDRESS'

```

#### includes/modules/pages/product_reviews_write/header_php.php
```
#14: 'NOTIFY_HEADER_START_PRODUCT_REVIEWS_WRITE'
#52: 'NOTIFY_REVIEWS_WRITE_CAPTCHA_CHECK'
#66: 'NOTIFY_SPAM_DETECTED_DURING_WRITE_REVIEW'
#87: 'NOTIFY_REVIEW_INSERTED_DURING_WRITE_REVIEW'
#100: 'NOTIFY_SEND_ADMIN_EMAIL_WRITE_REVIEW'
#112: 'NOTIFY_EMAIL_READY_WRITE_REVIEW'
#142: 'NOTIFY_HEADER_END_PRODUCT_REVIEWS_WRITE'

```

#### includes/modules/pages/product_music_info/main_template_vars.php
```
#14: 'NOTIFY_MAIN_TEMPLATE_VARS_START_PRODUCT_MUSIC_INFO'
#34: 'NOTIFY_PRODUCT_VIEWS_HIT_INCREMENTOR', (int)$_GET['products_id']
#109: 'NOTIFY_MAIN_TEMPLATE_VARS_PRODUCT_TYPE_VARS_PRODUCT_MUSIC_INFO'
#153: 'NOTIFY_MAIN_TEMPLATE_VARS_EXTRA_PRODUCT_MUSIC_INFO'
#161: 'NOTIFY_MAIN_TEMPLATE_VARS_END_PRODUCT_MUSIC_INFO'

```

#### includes/modules/pages/product_music_info/header_php.php
```
#11: 'NOTIFY_HEADER_START_PRODUCT_MUSIC_INFO'
#25: 'NOTIFY_HEADER_END_PRODUCT_MUSIC_INFO'

```

#### includes/modules/pages/product_music_info/main_template_vars_product_type.php
```
#17: 'NOTIFY_PRODUCT_TYPE_VARS_START_PRODUCT_MUSIC_INFO'
#70: 'NOTIFY_PRODUCT_TYPE_VARS_END_PRODUCT_MUSIC_INFO'

```

#### includes/modules/pages/product_reviews_info/header_php.php
```
#15: 'NOTIFY_HEADER_START_PRODUCT_REVIEWS_INFO'
#116: 'NOTIFY_HEADER_END_PRODUCT_REVIEWS_INFO'

```

#### includes/modules/pages/logoff/header_php.php
```
#11: 'NOTIFY_HEADER_START_LOGOFF'
#32: 'NOTIFY_HEADER_END_LOGOFF'

```

#### includes/modules/pages/redirect/header_php.php
```
#21: 'NOTIFY_BEFORE_REDIRECT_ACTION_PRODUCT', array(), $_GET['products_id'], $_SESSION['languages_id']
#29: 'NOTIFY_BEFORE_REDIRECT_ACTION_PRODUCT', array(), $_GET['products_id'], $_SESSION['languages_id']
#42: 'NOTIFY_BEFORE_REDIRECT_ACTION_MUSIC_ARTIST', array(), $_GET['artists_id'], $_SESSION['languages_id']
#51: 'NOTIFY_BEFORE_REDIRECT_ACTION_MUSIC_ARTIST', array(), $_GET['artists_id'], $_SESSION['languages_id']
#65: 'NOTIFY_BEFORE_REDIRECT_ACTION_RECORD_COMPANY', array(), $_GET['record_company_id'], $_SESSION['languages_id']
#74: 'NOTIFY_BEFORE_REDIRECT_ACTION_RECORD_COMPANY', array(), $_GET['record_company_id'], $_SESSION['languages_id']
#147: 'NOTIFY_REDIRECT_DEFAULT_ACTION'

```

#### includes/modules/pages/index/main_template_vars.php
```
#11: 'NOTIFY_HEADER_START_INDEX_MAIN_TEMPLATE_VARS'
#54: 'NOTIFY_HEADER_INDEX_MAIN_TEMPLATE_VARS_RELEASE_PRODUCT_TYPE_VARS'
#228: 'NOTIFY_HEADER_INDEX_MAIN_TEMPLATE_VARS_PAGE_BODY', NULL, $tpl_page_body, $current_categories_name
#233: 'NOTIFY_HEADER_END_INDEX_MAIN_TEMPLATE_VARS', NULL, $current_categories_description

```

#### includes/modules/pages/index/header_php.php
```
#11: 'NOTIFY_HEADER_START_INDEX'
#63:  'NOTIFY_INDEX_CATEGORY_STATUS_CHECK', ['cPath' => $cPath, 'current_category_id' => $current_category_id], $category_redirect_handled, $current_category_not_found, $current_category_is_disabled, $current_category_has_products, $current_category_has_subcats, $category_depth 
#146: 'NOTIFY_HEADER_END_INDEX'

```

#### includes/modules/pages/product_info/main_template_vars.php
```
#14: 'NOTIFY_MAIN_TEMPLATE_VARS_START_PRODUCT_INFO'
#34: 'NOTIFY_PRODUCT_VIEWS_HIT_INCREMENTOR', (int)$_GET['products_id']
#108: 'NOTIFY_MAIN_TEMPLATE_VARS_PRODUCT_TYPE_VARS_PRODUCT_INFO'
#152: 'NOTIFY_MAIN_TEMPLATE_VARS_EXTRA_PRODUCT_INFO'
#158: 'NOTIFY_MAIN_TEMPLATE_VARS_END_PRODUCT_INFO'

```

#### includes/modules/pages/product_info/header_php.php
```
#11: 'NOTIFY_HEADER_START_PRODUCT_INFO'
#25: 'NOTIFY_HEADER_END_PRODUCT_INFO'

```

#### includes/modules/pages/product_info/main_template_vars_product_type.php
```
#17: 'NOTIFY_PRODUCT_TYPE_VARS_START_PRODUCT_INFO'
#35: 'NOTIFY_PRODUCT_TYPE_VARS_END_PRODUCT_INFO'

```

#### includes/modules/pages/gv_faq/header_php.php
```
#11: 'NOTIFY_HEADER_START_GV_FAQ'
#45: 'NOTIFY_HEADER_END_GV_FAQ'

```

#### includes/modules/pages/account_notifications/header_php.php
```
#10: 'NOTIFY_HEADER_START_ACCOUNT_NOTIFICATION'
#136: 'NOTIFY_HEADER_END_ACCOUNT_NOTIFICATION'

```

#### includes/modules/pages/about_us/header_php.php
```
#10: 'NOTIFY_HEADER_START_ABOUT_US'
#18: 'NOTIFY_HEADER_END_ABOUT_US'

```

#### includes/modules/pages/address_book/header_php.php
```
#10: 'NOTIFY_HEADER_START_ADDRESS_BOOK'
#24: 'NOTIFY_HEADER_END_ADDRESS_BOOK'

```

#### includes/modules/pages/create_account/header_php.php
```
#11: 'NOTIFY_HEADER_START_CREATE_ACCOUNT'
#20: 'NOTIFY_HEADER_END_CREATE_ACCOUNT'

```

#### includes/modules/pages/account/header_php.php
```
#10: 'NOTIFY_HEADER_START_ACCOUNT'
#38: 'NOTIFY_HEADER_END_ACCOUNT'

```

#### includes/modules/pages/account_password/header_php.php
```
#10: 'NOTIFY_HEADER_START_ACCOUNT_PASSWORD'
#55: 'NOTIFY_HEADER_ACCOUNT_PASSWORD_CHANGED', $_SESSION['customer_id'], $password_new, $check_customer->fields['customers_nick']
#72: 'NOTIFY_HEADER_END_ACCOUNT_PASSWORD'

```

#### includes/modules/pages/checkout_shipping_address/header_php.php
```
#11: 'NOTIFY_HEADER_START_CHECKOUT_SHIPPING_ADDRESS'
#56: 'NOTIFY_HEADER_END_CHECKOUT_SHIPPING_ADDRESS'

```

#### includes/modules/pages/shopping_cart/header_php.php
```
#11: 'NOTIFY_HEADER_START_SHOPPING_CART'
#41: 'NOTIFY_HEADER_SHOPPING_CART_BEFORE_PRODUCTS_LOOP', null, $products
#92: 'NOTIFY_HEADER_SHOPPING_CART_IN_ATTRIBUTES_LOOP', $option, $attrArray, $attributes_values->fields, $value, $products, $i
#165: 'NOTIFY_HEADER_SHOPPING_CART_IN_PRODUCTS_LOOP', $i, $productArray
#169: 'NOTIFY_HEADER_SHOPPING_CART_AFTER_PRODUCTS_LOOP', $productArray
#191: 'NOTIFY_HEADER_END_SHOPPING_CART'

```

#### includes/modules/pages/account_edit/header_php.php
```
#10: 'NOTIFY_HEADER_START_ACCOUNT_EDIT'
#94: 'NOTIFY_NICK_CHECK_FOR_EXISTING_EMAIL', $email_address, $nick_error, $nick
#103: 'NOTIFY_HEADER_ACCOUNT_EDIT_VERIFY_COMPLETE'
#107: 'NOTIFY_NICK_UPDATE_EMAIL_ADDRESS', $nick, $email_address
#152: 'NOTIFY_HEADER_ACCOUNT_EDIT_UPDATES_COMPLETE'
#209: 'NOTIFY_HEADER_END_ACCOUNT_EDIT'

```

#### includes/modules/pages/site_map/header_php.php
```
#11: 'NOTIFY_HEADER_START_SITE_MAP'
#25: 'NOTIFY_HEADER_END_SITE_MAP'

```

#### includes/modules/pages/login/header_php.php
```
#10: 'NOTIFY_HEADER_START_LOGIN'
#69: 'NOTIFY_LOGIN_BANNED'
#85: 'NOTIFY_PROCESS_3RD_PARTY_LOGINS', $email_address, $password, $loginAuthorized
#105: 'NOTIFY_LOGIN_SUCCESS'
#139: 'NOTIFY_LOGIN_FAILURE'
#151: 'NOTIFY_HEADER_END_LOGIN'

```

#### includes/modules/pages/checkout_process/header_php.php
```
#10: 'NOTIFY_HEADER_START_CHECKOUT_PROCESS'
#17: 'NOTIFY_CHECKOUT_PROCESS_BEFORE_CART_RESET', $insert_id
#29: 'NOTIFY_HEADER_END_CHECKOUT_PROCESS', $insert_id

```

#### includes/modules/pages/address_book_process/header_php.php
```
#10: 'NOTIFY_HEADER_START_ADDRESS_BOOK_PROCESS'
#32: 'NOTIFY_HEADER_ADDRESS_BOOK_DELETION_DONE'
#169: 'NOTIFY_ADDRESS_BOOK_PROCESS_VALIDATION', array(), $error
#198: 'NOTIFY_MODULE_ADDRESS_BOOK_UPDATED_ADDRESS_BOOK_RECORD', array_merge(array('address_book_id' => $_GET['edit'], 'customers_id' => $_SESSION['customer_id']), $sql_data_array)
#216: 'NOTIFY_MODULE_ADDRESS_BOOK_UPDATED_CUSTOMER_RECORD', array_merge(array('customers_id' => $_SESSION['customer_id']), $sql_data_array)
#224: 'NOTIFY_MODULE_ADDRESS_BOOK_ADDED_ADDRESS_BOOK_RECORD', array_merge(array('address_id' => $new_address_book_id), $sql_data_array)
#246: 'NOTIFY_MODULE_ADDRESS_BOOK_UPDATED_PRIMARY_CUSTOMER_RECORD', array_merge(array('address_id' => $new_address_book_id, 'customers_id' => $_SESSION['customer_id']), $sql_data_array)
#348: 'NOTIFY_HEADER_END_ADDRESS_BOOK_PROCESS'

```

#### admin/packingslip.php
```
#68: 'NOTIFY_ADMIN_ORDERS_PACKINGSLIP_ADDITIONAL_DATA_TOP', $oID, $additional_content
#166: 'NOTIFY_ADMIN_PACKINGSLIP_HEADING', '', $extra_headings
#186: 'NOTIFY_ADMIN_PACKINGSLIP_SORT_DISPLAY', $order->products, $sort_order
#260: 'NOTIFY_ADMIN_PACKINGSLIP_DATA',  $order->products[$i]['id'], $extra_data
#334: 'NOTIFY_ADMIN_ORDERS_PACKINGSLIP_ADDITIONAL_DATA_BOTTOM', $oID, $additional_content

```

#### admin/attributes_controller.php
```
#334: 'NOTIFY_ATTRIBUTE_CONTROLLER_ADD_PRODUCT_ATTRIBUTES', $products_attributes_id
#479: 'NOTIFY_ATTRIBUTE_CONTROLLER_UPDATE_PRODUCT_ATTRIBUTE', $attribute_id
#492: 'NOTIFY_ATTRIBUTE_CONTROLLER_DELETE_ATTRIBUTE', ['attribute_id' => $attribute_id], $attribute_id
#509: 'NOTIFY_ATTRIBUTE_CONTROLLER_DELETE_ALL', ['pID' => $_POST['products_filter']]
#523: 'NOTIFY_ATTRIBUTE_CONTROLLER_DELETE_OPTION_NAME_VALUES', ['pID' => $_POST['products_filter'], 'options_id' => $_POST['products_options_id_all']]
#681: 'NOTIFY_ATTRIBUTE_CONTROLLER_ADDITIONAL_ACTIONS_DROPDOWN_UPPER', $zc_products, $action, $products_filter, $current_category_id
#687: 'NOTIFY_ATTRIBUTE_CONTROLLER_ADDITIONAL_ACTIONS_DROPDOWN_SUBMENU', $zc_products, $action, $products_filter, $current_category_id

```

#### admin/product.php
```
#14: 'NOTIFY_BEGIN_ADMIN_PRODUCTS', $action, $action

```

#### admin/languages.php
```
#178: 'NOTIFY_ADMIN_LANGUAGE_INSERT', (int)$insert_id
#255: 'NOTIFY_ADMIN_LANGUAGE_DELETE', (int)$lID

```

#### admin/category_product_listing.php
```
#308: 'NOTIFY_ADMIN_PROD_LISTING_DEFAULT_ACTION'
#602: 'NOTIFY_ADMIN_PROD_LISTING_HEADERS_B4_QTY', '', $extra_headings
#637: 'NOTIFY_ADMIN_PROD_LISTING_HEADERS_AFTER_QTY', '', $extra_headings
#720: 'NOTIFY_ADMIN_PROD_LISTING_ADD_ICON_CATEGORY', $category, $additional_icons
#792: 'NOTIFY_ADMIN_PROD_LISTING_PRODUCTS_QUERY', '', $extra_select, $extra_from, $extra_joins, $extra_ands, $order_by
#892: 'NOTIFY_ADMIN_PROD_LISTING_DATA_B4_QTY', $product, $extra_data
#923: 'NOTIFY_ADMIN_PROD_LISTING_DATA_AFTER_QTY', $product, $extra_data
#936: 'NOTIFY_ADMIN_PROD_LISTING_ADD_ICON', $product, $additional_icons

```

#### admin/admin_activity.php
```
#305: 'NOTIFY_ADMIN_ACTIVITY_LOG_RESET'

```

#### admin/includes/classes/class.admin.zcObserverLogEventListener.php
```
#59: $this->notifier->notify('NOTIFY_ADMIN_FIRE_LOG_WRITERS', $log_data
#194: $this->notifier->notify('NOTIFY_ADMIN_FIRE_LOG_WRITER_RESET'
#210: 'NOTIFY_ADMIN_ACTIVITY_LOG_EVENT', $message, $severity

```

#### admin/includes/init_includes/init_sanitize.php
```
#269: 'NOTIFY_ADMIN_CONFIGURATION_SPECIAL_CHARACTERS', [], $extra_configs_with_special_characters

```

#### admin/includes/init_includes/init_languages.php
```
#21: 'NOTIFY_LANGUAGE_CHANGE_REQUESTED_BY_ADMIN_VISITOR', $_GET['language'], $lng

```

#### admin/includes/init_includes/init_admin_history.php
```
#11: 'NOTIFY_ADMIN_ACTIVITY_LOG_EVENT', 'POST'

```

#### admin/includes/init_includes/init_admin_auth.php
```
#71: 'NOTIFY_ADMIN_NONSUPERUSER_ACTION'

```

#### admin/includes/attributes_preview.php
```
#94: 'NOTIFY_ATTRIBUTES_MODULE_START_OPTION', $products_options_names->fields
#104: 'NOTIFY_ATTRIBUTES_MODULE_START_OPTIONS_LOOP', array(), $products_options->fields
#593: 'NOTIFY_ATTRIBUTES_MODULE_DEFAULT_SWITCH', $products_options_names->fields, $options_name, $options_menu, $options_comment, $options_comment_position, $options_html_id
#600: 'NOTIFY_ATTRIBUTES_MODULE_OPTION_BUILT', $products_options_names->fields, $options_name, $options_menu, $options_comment, $options_comment_position, $options_html_id, $options_attributes_image

```

#### admin/includes/footer.php
```
#26: 'NOTIFY_ADMIN_FOOTER_END'

```

#### admin/includes/functions/html_output.php
```
#14:  'NOTIFY_HANDLE_ADMIN_HREF_LINK', array( 'page' => $page, 'parameters' => $parameters, 'add_session_id' => false, ), $page, $parameters 
#70: 'NOTIFY_SEFU_INTERCEPT_ADMCATHREF', array(), $link, $page, $parameters, $connection
#109: 'NOTIFY_SEFU_INTERCEPT_ADMCATHOME', array(), $link, $connection

```

#### admin/includes/functions/functions_help.php
```
#168: 'NOTIFIER_PLUGIN_HELP_PAGE_URL_LOOKUP', $page, $help_page

```

#### admin/includes/functions/general.php
```
#399: 'NOTIFIER_ADMIN_ZEN_REMOVE_ORDER', array(), $order_id, $restock

```

#### admin/includes/modules/new_product_preview.php
```
#23: 'NOTIFY_ADMIN_PRODUCT_IMAGE_UPLOADED', $products_image, $products_image_name

```

#### admin/includes/modules/update_product.php
```
#29: 'NOTIFY_MODULES_UPDATE_PRODUCT_START', ['action' => $action, 'products_id' => $products_id]
#130: 'NOTIFY_MODULES_UPDATE_PRODUCT_END', array('action' => $action, 'products_id' => $products_id)

```

#### admin/includes/modules/product_free_shipping/collect_info.php
```
#209: 'NOTIFY_ADMIN_PRODUCT_COLLECT_INFO_EXTRA_INPUTS', $pInfo, $extra_product_inputs

```

#### admin/includes/modules/document_general/collect_info.php
```
#219: 'NOTIFY_ADMIN_PRODUCT_COLLECT_INFO_EXTRA_INPUTS', $pInfo, $extra_product_inputs

```

#### admin/includes/modules/document_product/collect_info.php
```
#209: 'NOTIFY_ADMIN_PRODUCT_COLLECT_INFO_EXTRA_INPUTS', $pInfo, $extra_product_inputs

```

#### admin/includes/modules/product/collect_info.php
```
#212: 'NOTIFY_ADMIN_PRODUCT_COLLECT_INFO_EXTRA_INPUTS', $pInfo, $extra_product_inputs

```

#### admin/includes/modules/copy_product_confirm.php
```
#65: 'NOTIFY_MODULES_COPY_PRODUCT_CONFIRM_DUPLICATE_FIELDS', $product, $separately_updated_fields, $casted_fields
#204: 'NOTIFY_MODULES_COPY_TO_CONFIRM_DUPLICATE', compact('products_id', 'dup_products_id')

```

#### admin/includes/modules/product_music/collect_info.php
```
#242: 'NOTIFY_ADMIN_PRODUCT_COLLECT_INFO_EXTRA_INPUTS', $pInfo, $extra_product_inputs

```

#### admin/includes/modules/copy_product.php
```
#49: 'NOTIFY_ADMIN_PRODUCT_COPY_TO_ATTRIBUTES', $pInfo, $contents

```

#### admin/options_values_manager.php
```
#133: 'OPTIONS_VALUES_MANAGER_DELETE_VALUE', array('value_id' => $value_id)
#445: 'OPTIONS_VALUES_MANAGER_DELETE_VALUES_OF_OPTIONNAME', array('current_products_id' => $current_products_id, 'remove_ids' => $remove_downloads_ids, 'options_id' => $options_id_from, 'options_values_id' => $options_values_values_id_from)

```

#### admin/invoice.php
```
#75: 'NOTIFY_ADMIN_ORDERS_INVOICE_ADDITIONAL_DATA_TOP', $oID, $additional_content
#173: 'NOTIFY_ADMIN_INVOICE_HEADING_B4_TAX', '', $extra_headings
#214: 'NOTIFY_ADMIN_INVOIVE_HEADERS_AFTER_TAX', '', $extra_headings
#235: 'NOTIFY_ADMIN_INVOICE_SORT_DISPLAY', $order->products, $sort_order
#320: 'NOTIFY_ADMIN_INVOICE_DATA_B4_TAX',  $order->products[$i]['id'], $extra_data
#376: 'NOTIFY_ADMIN_INVOICE_DATA_AFTER_TAX', $order->products[$i]['id'], $extra_data
#466: 'NOTIFY_ADMIN_ORDERS_INVOICE_ADDITIONAL_DATA_BOTTOM', $oID, $additional_content

```

#### admin/whos_online.php
```
#206: 'ADMIN_WHOSONLINE_IP_LINKS', $item, $additional_ipaddress_links, $whois_url

```

#### admin/ezpages.php
```
#105: 'NOTIFY_ADMIN_EZPAGES_UPDATE_BASE', $action, $page_error, $sql_data_array
#139: 'NOTIFY_ADMIN_EZPAGES_UPDATE_LANG_INSERT', array('pages_id' => (int)$pages_id, 'languages_id' => $language_id), $sql_data_array
#156: 'NOTIFY_ADMIN_EZPAGES_UPDATE_LANG_UPDATE', array('pages_id' => (int)$pages_id, 'languages_id' => $language_id), $sql_data_array
#268: 'NOTIFY_ADMIN_EZPAGES_NEW', '', $parameters
#342: 'NOTIFY_ADMIN_EZPAGES_FORM_FIELDS', $ezInfo, $extra_page_inputs
#720: 'NOTIFY_ADMIN_EZPAGES_EXTRA_ACTION_ICONS', $page, $extra_action_icons

```

#### admin/coupon_admin.php
```
#106: 'ADMIN_COUPON_CODE_EMAILED_TO_CUSTOMER', $coupon_result->fields['coupon_code'], $item['customers_email_address']

```

#### admin/categories.php
```
#40: 'NOTIFY_BEGIN_ADMIN_CATEGORIES', $action
#193: 'NOTIFY_ADMIN_CATEGORIES_UPDATE_OR_INSERT_FINISH', ['action' => $action, 'categories_id' => (int)$categories_id]
#352: 'NOTIFY_ADMIN_CATEGORIES_EXTRA_INPUTS', $cInfo, $extra_category_inputs

```

#### admin/customers.php
```
#190: 'NOTIFY_ADMIN_CUSTOMERS_UPDATE_VALIDATE', array(), $error
#259: 'NOTIFY_ADMIN_CUSTOMERS_CUSTOMER_UPDATE', $customers_id, $sql_data_array
#326:  'NOTIFY_ADMIN_CUSTOMERS_B4_ADDRESS_UPDATE', array('customers_id' => $customers_id, 'address_book_id' => $default_address_id), $sql_data_array 
#350:  'NOTIFY_ADMIN_CUSTOMER_UPDATE', (int)$customers_id, $default_address_id, $sql_data_array 
#442: 'NOTIFIER_ADMIN_ZEN_CUSTOMERS_DELETE_CONFIRM', array('customers_id' => $customers_id) 
#686: 'NOTIFY_ADMIN_CUSTOMERS_CUSTOMER_EDIT', $cInfo, $additional_fields
#1316:  'NOTIFY_ADMIN_CUSTOMERS_LISTING_HEADER', array(), $additional_headings 
#1467:  'NOTIFY_ADMIN_CUSTOMERS_LISTING_NEW_FIELDS', array(), $new_fields, $disp_order 
#1590:  'NOTIFY_ADMIN_CUSTOMERS_LISTING_ELEMENT', $customer, $additional_columns 
#1823:  'NOTIFY_ADMIN_CUSTOMERS_PLACE_ORDER_BUTTON', $cInfo, $contents, $place_order_override 
#1867: 'NOTIFY_ADMIN_CUSTOMERS_MENU_BUTTONS', $cInfo, $contents
#1920:  'NOTIFY_ADMIN_CUSTOMERS_MENU_BUTTONS_END', (isset($cInfo) ? $cInfo : new stdClass), $contents 

```

#### admin/orders.php
```
#80: 'NOTIFY_ADMIN_ORDER_PREDISPLAY_HOOK', $oID, $action
#243: 'NOTIFY_ADMIN_ORDERS_UPDATE_ORDER_START', $oID
#392: 'NOTIFY_ADMIN_ORDERS_DEFAULT_ACTION', $oID, $order, $action
#432: 'NOTIFY_ADMIN_ORDERS_HEADING_TITLE', ['action' => $action, 'order_exists' => $order_exists, 'oID' => $oID], $heading_title, $extra_top_content
#508: 'NOTIFY_ADMIN_ORDERS_EDIT_BEGIN', $oID, $order
#556: 'NOTIFY_ADMIN_ORDERS_UPPER_BUTTONS', $oID, $left_side_buttons, $right_side_buttons
#598: 'NOTIFY_ADMIN_ORDERS_ADDRESS_FOOTERS', 'customer', $address_footer_suffix, $order->customer
#621: 'ADMIN_ORDERS_IP_LINKS', $lookup_ip, $whois_url
#648: 'NOTIFY_ADMIN_ORDERS_ADDRESS_FOOTERS', 'delivery', $address_footer_suffix, $order->delivery
#667: 'NOTIFY_ADMIN_ORDERS_ADDRESS_FOOTERS', 'billing', $address_footer_suffix, $order->billing
#734: <?php 'NOTIFY_ADMIN_ORDERS_PAYMENTDATA_COLUMN2', $oID, $order ?>
#866: 'NOTIFY_ADMIN_ORDERS_CONTENT_UNDER_PRODUCTS', ['oID' => $oID], $extra_content
#898: 'NOTIFY_ADMIN_ORDERS_STATUS_HISTORY_EXTRA_COLUMN_HEADING', [], $extra_headings
#952: 'NOTIFY_ADMIN_ORDERS_STATUS_HISTORY_EXTRA_COLUMN_DATA', $orders_history->fields, $extra_data
#989: 'NOTIFY_ADMIN_ORDERS_AFTER_STATUS_LISTING', $oID, $additional_content
#1013: 'NOTIFY_ADMIN_ORDERS_ADDL_HISTORY_INPUTS', []
#1035: 'NOTIFY_ADMIN_ORDERS_EXTRA_STATUS_INPUTS', $order, $extra_status_inputs
#1083: 'NOTIFY_ADMIN_ORDERS_EDIT_BUTTONS', $oID, $order, $extra_buttons
#1113: 'NOTIFY_ADMIN_ORDERS_MENU_LEGEND', [], $extra_legends
#1177: 'NOTIFY_ADMIN_ORDERS_LIST_EXTRA_COLUMN_HEADING', [], $extra_headings
#1242: 'NOTIFY_ADMIN_ORDERS_SEARCH_PARMS', $keywords, $search, $search_distinct, $new_fields, $new_table, $order_by
#1305: 'NOTIFY_ADMIN_ORDERS_SHOW_ORDER_DIFFERENCE', [], $orders->fields, $show_difference, $extra_action_icons
#1385: 'NOTIFY_ADMIN_ORDERS_LIST_EXTRA_COLUMN_DATA', ($oInfo ?? []), $orders->fields, $extra_data
#1461: 'NOTIFY_ADMIN_ORDERS_MENU_BUTTONS', $oInfo, $contents
#1539: 'NOTIFY_ADMIN_ORDERS_MENU_BUTTONS_END', ($oInfo ?? []), $contents

```

#### admin/options_name_manager.php
```
#182: 'OPTIONS_NAME_MANAGER_DELETE_OPTION', ['option_id' => $option_id, 'options_values_id' => (int)$remove_option_value['products_options_values_id']]
#301: 'OPTIONS_NAME_MANAGER_UPDATE_OPTIONS_VALUES_DELETE', [ 'products_id' => $all_update_product['products_id'], 'options_id' => $all_options_value['products_options_id'], 'options_values_id' => $all_options_value['products_options_values_id'] ] 

```

#### notifier_report.php
```
#46: // Determine if the current line contains a '->notify', continuing if not. // $next_pos = strpos($lines[$i], '->notify'
#71: '', '', '', '$GLOBALS[\'zco_notifier\']->notify(', '',

```

#### not_for_release/testFramework/Unit/testsNotifiers/NotifierUpdateHandlersTest.php
```
#30: $this->base->notify('NOTIFY_TEST_SNAKE_CASE', null, $testVar
#34: $this->base->notify('NOTIFY_TEST_CAMEL_CASE', null, $testVar
#38: $this->base->notify('NOTIFY_TEST_UPDATE', null, $testVar

```

#### not_for_release/testFramework/Support/zcNotifierTraitAliasTestObject.php
```
#13: 'NOTIFY_ORDER_CART_SUBTOTAL_CALCULATE'
#20: 'NOTIFIYFOO_ORDER_CART_SUBTOTAL_CALCULATE'

```

#### not_for_release/testFramework/Support/zcNotifierBaseAliasTestObject.php
```
#10: 'NOTIFY_ORDER_CART_SUBTOTAL_CALCULATE'
#17: 'NOTIFIYFOO_ORDER_CART_SUBTOTAL_CALCULATE'
