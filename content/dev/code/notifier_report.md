---
title: Notifier Report for Zen Cart 2.1.0
description: Output of the Zen Cart Notifier Report plugin 
category: code
type: codepage
weight: 10
---

<!-- RELEASETIME - update -->


#### ipn_main_handler.php
```
#363: 'NOTIFY_CHECKOUT_PROCESS_BEFORE_ORDER_TOTALS_PROCESS'
#365: 'NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_TOTALS_PROCESS'
#377: 'NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_CREATE'
#384: 'NOTIFY_CHECKOUT_PROCESS_AFTER_PAYMENT_MODULES_AFTER_ORDER_CREATE'
#411: 'NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_CREATE_ADD_PRODUCTS'
#414: 'NOTIFY_CHECKOUT_PROCESS_AFTER_SEND_ORDER_EMAIL'
#458: 'NOTIFY_CHECKOUT_PROCESS_HANDLE_AFFILIATES', 'paypalipn'
#554: 'NOTIFY_PAYPALIPN_STATUS_HISTORY_UPDATE', [$ordersID, $new_status, $txn_type]

```

#### zc_plugins/POSM/v6.0.0/catalog/includes/classes/observers/class.products_options_stock_observer.php
```
#109: 'NOTIFY_PRODUCTS_OPTIONS_STOCK_OBSERVER_INSTANTIATED'
#185:  'NOTIFY_POSM_ORDER_STOCK_DECREMENT_BEGIN', [ 'product' => $order->products[$i], 'stock' => $stock_record ], $bypass_stock_decrement, $decrement_options_stock 
#263:  'NOTIFY_POSM_ORDER_ADDED_PRODUCT_LINE_ITEM', [ 'product' => $ordered_product, 'stock' => $pos_record, ], $decrement_stock, $decrement_managed_stock 
#618:  'NOTIFY_POSM_GET_IN_STOCK_MESSAGE', [ 'prid' => $prid, 'pos_record' => $pos_record, ], $message_override, $use_in_stock_message, $show_mixed_stock_messages 

```

#### zc_plugins/POSM/v6.0.0/catalog/includes/classes/ajax/zcAjaxOptionsStockDependencies.php
```
#109: 'NOTIFY_AJAX_POSM_DEPENDENCIES_SELECT_CLAUSE', '', $select_clause
#121: 'NOTIFY_AJAX_POSM_DEPENDENCIES_EXTRA_INFO', $attr_info->fields, $extra_info
#145: 'NOTIFY_AJAX_POSM_DEPENDENCIES_EXTENSION_INFO', $option_values, $extra_functions

```

#### zc_plugins/POSM/v6.0.0/catalog/includes/templates/default/jscript/posm_dependencies_jscript.php
```
#37: 'NOTIFY_POSM_DEPENDENCIES_ENABLE_OVERRIDE', [], $posm_dependent_attrs_enable

```

#### zc_plugins/POSM/v6.0.0/admin/products_options_stock_view_all.php
```
#30: 'NOTIFY_POSM_VIEW_ALL_UPDATE_INIT'
#74: 'NOTIFY_POSM_VIEW_ALL_UPDATE', $pos_id, $posm_sql_data, $where_str, $error, $onload
#102: 'NOTIFY_POSM_VIEW_ALL_UPDATE_PRODUCT', $product['products_id']
#218: 'NOTIFY_POSM_VIEW_ALL_INSERT_HEAD', '', $onload, $css_content, $js_content
#241: 'NOTIFY_POSM_VIEW_ALL_START_BODY', '', $static_field_count, $instructions2
#301: 'NOTIFY_POSM_VIEW_ALL_TABLE_HEADING', '', $additional_content
#380:  'NOTIFY_POSM_VIEW_ALL_PRODUCTS_NAME', $products_id, $products_name_extra_info, $additional_content 
#490: 'NOTIFY_POSM_VIEW_ALL_INSERT_DATA', $current_option['fields'], $additional_content

```

#### zc_plugins/POSM/v6.0.0/admin/includes/classes/observers/class.products_options_stock_admin_observer.php
```
#187:  'NOTIFY_POSM_EO_ADD_PRODUCT_BYPASS', $info, $bypass_add 
#270:  'NOTIFY_POSM_EO_PRODUCT_ADD_STOCK_UPDATE', [ 'pos_record' => $pos_record, 'product' => $info ], $bypass_managed_stock_update 
#860:  'NOTIFY_POSM_EO_REMOVE_PRODUCT_QUANTITY_BYPASS', $orders_products_id, $bypass_quantity_updates 
#979:  'NOTIFY_POSM_GET_IN_STOCK_MESSAGE_BYPASS', [ 'op_info' => $op_info, 'prod_info' => $prod_info, 'pos_info' => $check, ], $msg_text_override, $force_out_of_stock_message 

```

#### zc_plugins/POSM/v6.0.0/admin/includes/functions/products_options_stock_admin_functions.php
```
#199:  'POSM_MAIN_OPTION_INSERTED', [ 'pID' => $pID, 'options_values_array' => $options_values_array, 'quantity' => $quantity, 'pos_id' => $pos_id ] 

```

#### zc_plugins/POSM/v6.0.0/admin/products_options_stock.php
```
#163: 'NOTIFY_POSM_UPDATE_PREPARE_INPUTS', $qty_count, $missing_inputs_flag, $error, $onload
#229:  'NOTIFY_POSM_UPDATE_DATABASE_RECORD', [ 'pos_id' => $pos_id, 'pID' => $pID, ], $update_posm_record_sql, $error, $onload 
#270: 'NOTIFY_POSM_REMOVE_OPTIONS', $pID
#527: 'NOTIFY_POSM_INSERT_HEAD', '', $onload, $css_content, $js_content
#648: 'NOTIFY_POSM_ADD_PRODUCT_OPTION', $next_option, $pos_product_options
#697: 'NOTIFY_POSM_START_HTML_OUTPUT', [], $static_field_count
#889: 'NOTIFY_POSM_UPPER_HEADING_INSERT', '', $additional_content
#944: 'NOTIFY_POSM_UPPER_CONTENT_INSERT', '', $additional_content
#1040: 'NOTIFY_POSM_SET_INSTRUCTIONS', $pID, $additional_instructions
#1091: 'NOTIFY_POSM_LOWER_HEADING_INSERT_B4_QTY', '', $extra_headings
#1130: 'NOTIFY_POSM_LOWER_HEADING_INSERT_AFTER_QTY', '', $extra_headings
#1190: 'NOTIFY_POSM_SET_UPDATE_BUTTON_PARAMETERS', '', $posm_update_button_parms
#1308:  'NOTIFY_POSM_LOWER_CONTENT_INSERT_B4_QTY', [ 'pos_id' => $pos_id, 'info_array' => $info_array, 'action' => $action, ], $lower_content 
#1354:  'NOTIFY_POSM_LOWER_CONTENT_INSERT_AFTER_QTY', [ 'pos_id' => $pos_id, 'info_array' => $info_array, 'action' => $action, ], $lower_content 

```

#### includes/classes/shopping_cart.php
```
#84: 'NOTIFIER_CART_INSTANTIATE_START'
#86: 'NOTIFIER_CART_INSTANTIATE_END'
#106: 'NOTIFIER_CART_RESTORE_CONTENTS_START'
#191: 'NOTIFIER_CART_RESTORE_CONTENTS_END'
#209: 'NOTIFIER_CART_RESET_START', null, $reset_database
#233: 'NOTIFIER_CART_RESET_END'
#281: 'NOTIFIER_CART_ADD_CART_START', null, $product_id, $qty, $attributes, $notify
#378: 'NOTIFIER_CART_ADD_CART_END', null, $product_id, $qty, $attributes, $notify
#409: 'NOTIFIER_CART_UPDATE_QUANTITY_START', null, $uprid, $quantity, $attributes
#492: 'NOTIFIER_CART_UPDATE_QUANTITY_END'
#507: 'NOTIFIER_CART_CLEANUP_START'
#513: 'NOTIFIER_CART_CLEANUP_END'
#555: 'NOTIFIER_CART_COUNT_CONTENTS_START'
#562: 'NOTIFIER_CART_COUNT_CONTENTS_END'
#577: 'NOTIFIER_CART_GET_QUANTITY_START', null, $uprid
#579: 'NOTIFIER_CART_GET_QUANTITY_END_QTY', null, $uprid
#583: 'NOTIFIER_CART_GET_QUANTITY_END_FALSE', $uprid
#595: 'NOTIFIER_CART_IN_CART_START', null, $uprid
#597: 'NOTIFIER_CART_IN_CART_END_TRUE', null, $uprid
#601: 'NOTIFIER_CART_IN_CART_END_FALSE', $uprid
#613: 'NOTIFIER_CART_REMOVE_START', null, $uprid
#618: 'NOTIFIER_CART_REMOVE_END'
#626: 'NOTIFIER_CART_REMOVE_ALL_START'
#628: 'NOTIFIER_CART_REMOVE_ALL_END'
#685: 'NOTIFY_CART_CALCULATE_PRODUCT_PRICE', $uprid, $product
#750: 'NOTIFY_CART_CALCULATE_ATTRIBUTE_PRICE', $uprid, $attribute_price->fields
#940: 'NOTIFY_CART_CALCULATE_ATTRIBUTE_WEIGHT', ['products_id' => $uprid, 'options_id' => $option], $attribute_weight->fields
#1002: 'NOTIFY_CART_ATTRIBUTES_PRICE_START', $uprid
#1021: 'NOTIFY_CART_ATTRIBUTES_PRICE_NEXT', $uprid, $attribute_price
#1122: 'NOTIFY_CART_ATTRIBUTES_PRICE_ONETIME_CHARGES_START', $uprid
#1137: 'NOTIFY_CART_ATTRIBUTES_PRICE_ONETIME_CHARGES_NEXT', $uprid, $attribute_price
#1187: 'NOTIFY_CART_ATTRIBUTES_WEIGHT_START', $uprid
#1197: 'NOTIFY_CART_ATTRIBUTES_WEIGHT_NEXT', $uprid, $attribute_weight_info->fields
#1223: 'NOTIFIER_CART_GET_PRODUCTS_START', null, $check_for_valid_cart
#1238: 'NOTIFY_CART_GET_PRODUCTS_NEXT', $uprid, $product
#1411: 'NOTIFIER_CART_GET_PRODUCTS_END', null, $products_array
#1422: 'NOTIFIER_CART_SHOW_TOTAL_START'
#1424: 'NOTIFIER_CART_SHOW_TOTAL_END'
#1435: 'NOTIFIER_CART_SHOW_TOTAL_BEFORE_DISCOUNT_START'
#1437: 'NOTIFIER_CART_SHOW_TOTAL_BEFORE_DISCOUNT_END'
#1885: 'NOTIFIER_CART_OPTIONAL_SUCCESS_UPDATED_CART', $_POST, $goto, $parameters
#2089: 'NOTIFIER_CART_OPTIONAL_SUCCESS_PRODUCT_ADDED_TO_CART', $_POST, $goto, $parameters
#2097: 'NOTIFIER_CART_OPTIONAL_ATTRIBUTE_ERROR_MESSAGE_HOOK', $_POST, $the_list
#2154: 'NOTIFIER_CART_OPTIONAL_SUCCESS_BUYNOW_ADDED_TO_CART', $_GET, $goto, $parameters
#2243: 'NOTIFIER_CART_OPTIONAL_SUCCESS_MULTIPLE_ADDED_TO_CART', $products_list, $goto, $parameters
#2366: 'NOTIFY_CART_USER_ACTION', null, $goto, $parameters

```

#### includes/classes/Category.php
```
#155: 'NOTIFY_GET_CATEGORY_OBJECT_DETAILS', $category_id, $data

```

#### includes/classes/Product.php
```
#148: 'NOTIFY_GET_PRODUCT_ALLOW_ADD_TO_CART', $this->product_id, $allow_add_to_cart, $this->data
#157: 'NOTIFY_GET_PRODUCT_QUANTITY', $this->product_id, $quantity
#228: 'NOTIFY_GET_PRODUCT_OBJECT_DETAILS_NOT_FOUND', ['product_id' => $product_id, 'language_id' => $language_id], $data_override
#273: 'NOTIFY_GET_PRODUCT_OBJECT_DETAILS', $product_id, $data

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
#201: 'NOTIFY_ORDER_COUPON_LINK', $coupon_link->fields, $zc_coupon_link
#363: 'NOTIFY_ORDER_QUERY_ADD_PRODUCT', $this->products[$index], $index
#371: 'NOTIFY_ORDER_AFTER_QUERY', IS_ADMIN_FLAG, $this->orderId
#377: 'ORDER_QUERY_ADMIN_COMPLETE', ['orders_id' => $this->orderId]
#464: 'NOTIFY_ORDER_CART_BEGINS'
#575: 'NOTIFY_ORDER_CART_ADDRESS_OVERRIDES', [], $customer_address_override, $delivery_address_override, $billing_address_override
#681: 'NOTIFY_ORDER_CART_AFTER_ADDRESSES_SET', '', $taxCountryId, $taxZoneId
#719: 'NOTIFY_ORDER_CART_ADD_PRODUCT_LIST', ['index' => $index, 'products' => $products[$i]], $attributes_handled
#757: 'NOTIFY_ORDER_CART_ADD_ATTRIBUTE_LIST', ['index' => $index, 'subindex' => $subindex, 'products' => $products[$i], 'attributes' => $attributes]
#797: 'NOTIFY_ORDER_CART_FINISHED'
#850: 'NOTIFY_ORDER_CART_EXTERNAL_TAX_RATE_LOOKUP', STORE_PRODUCT_TAX_BASIS, $products, $loop, $index, $taxCountryId, $taxZoneId, $taxRates
#899: 'NOTIFY_ORDER_CART_SUBTOTAL_CALCULATE', ['shown_price' => $shown_price]
#935: 'NOTIFY_ORDER_CART_EXTERNAL_TAX_DURING_ORDER_CREATE', [], $zf_ot_modules
#946: 'NOTIFY_ORDER_CART_ORDERSTATUS'
#1014: 'NOTIFY_ORDER_DURING_CREATE_ADDED_ORDER_HEADER', array_merge(['orders_id' => $this->orderId, 'shipping_weight' => $_SESSION['cart']->weight], $sql_data_array), $this->orderId
#1028: 'NOTIFY_ORDER_DURING_CREATE_ADDED_ORDERTOTAL_LINE_ITEM', $sql_data_array, $ot_insert_id
#1056: 'NOTIFY_ORDER_DURING_CREATE_ADDED_ORDER_COMMENT', $sql_data_array, $osh_insert_id
#1084: 'NOTIFY_ORDER_PROCESSING_STOCK_DECREMENT_INIT', ['i' => $i], $this->products[$i], $i
#1108: 'NOTIFY_ORDER_PROCESSING_STOCK_DECREMENT_BEGIN', $i, $stock_values
#1135: 'NOTIFY_ORDER_PROCESSING_BESTSELLERS_UPDATE', [], $this->products[$i], $i
#1140: 'NOTIFY_ORDER_PROCESSING_STOCK_DECREMENT_END', $i
#1170: 'NOTIFY_ORDER_DURING_CREATE_ADDED_PRODUCT_LINE_ITEM', array_merge(['orders_products_id' => $order_products_id, 'i' => $i], $sql_data_array), $order_products_id
#1172: 'NOTIFY_ORDER_PROCESSING_CREDIT_ACCOUNT_UPDATE_BEGIN'
#1175: 'NOTIFY_ORDER_PROCESSING_ATTRIBUTES_BEGIN'
#1269: 'NOTIFY_ORDER_DURING_CREATE_ADDED_ATTRIBUTE_LINE_ITEM', array_merge(['orders_products_attributes_id' => $opa_insert_id], $sql_data_array), $opa_insert_id
#1284: 'NOTIFY_ORDER_DURING_CREATE_ADDED_ATTRIBUTE_DOWNLOAD_LINE_ITEM', $sql_data_array, $opd_insert_id
#1290: 'NOTIFY_ORDER_PROCESSING_ATTRIBUTES_EXIST', $attributes_exist
#1292: 'NOTIFY_ORDER_DURING_CREATE_ADD_PRODUCTS', $i, $custom_insertable_text
#1320: 'NOTIFY_ORDER_PROCESSING_ONE_TIME_CHARGES_BEGIN', $i
#1341: 'NOTIFY_ORDER_AFTER_ORDER_CREATE_ADD_PRODUCTS'
#1354: 'NOTIFY_ORDER_SEND_EMAIL_INITIALIZE', [], $zf_insert_id, $order_totals, $zf_mode
#1357: 'NOTIFY_ORDER_SEND_LOW_STOCK_EMAILS'
#1397: 'NOTIFY_ORDER_EMAIL_BEFORE_PRODUCTS', [], $email_order, $html_msg
#1463: 'NOTIFY_ORDER_SET_ORDER_MESSAGE'
#1485: 'NOTIFY_ORDER_INVOICE_CONTENT_READY_TO_SEND', ['zf_insert_id' => $zf_insert_id, 'text_email' => $email_order, 'html_email' => $html_msg], $email_order, $html_msg, $send_customer_email
#1507: 'NOTIFY_ORDER_INVOICE_CONTENT_FOR_ADDITIONAL_EMAILS', $zf_insert_id, $email_order, $html_msg, $sendExtraOrderEmail
#1519: 'NOTIFY_ORDER_AFTER_SEND_ORDER_EMAIL', $zf_insert_id, $email_order, $extra_info, $html_msg

```

#### includes/classes/shipping.php
```
#48: 'NOTIFY_SHIPPING_CLASS_GET_INSTALLED_MODULES', $module
#108: 'NOTIFY_SHIPPING_MODULE_ENABLE', $quote_module['class'], $quote_module['class']
#145: 'NOTIFY_SHIPPING_CHECK_ENABLED_FOR_ZONE', [], $module_class, $enabled
#150: 'NOTIFY_SHIPPING_CHECK_ENABLED', [], $module_class, $enabled
#166: 'NOTIFY_SHIPPING_MODULE_PRE_CALCULATE_BOXES_AND_TARE', [], $total_weight, $shipping_weight, $shipping_quoted, $shipping_num_boxes
#208: 'NOTIFY_SHIPPING_MODULE_CALCULATE_BOXES_AND_TARE', [], $total_weight, $shipping_weight, $shipping_quoted, $shipping_num_boxes
#266: 'NOTIFY_SHIPPING_MODULE_GET_ALL_QUOTES', $quotes_array, $quotes_array
#321: 'NOTIFY_SHIPPING_EXCLUDE_FROM_CHEAPEST', $rate['module'], $exclude_from_cheapest
#331: 'NOTIFY_SHIPPING_MODULE_CALCULATE_CHEAPEST', $cheapest, $cheapest, $rates

```

#### includes/classes/class.search.php
```
#110: 'NOTIFY_ADVANCED_SEARCH_RESULTS_ADDL_CLAUSE', [], $search_additional_clause
#225: 'NOTIFY_SEARCH_COLUMNLIST_STRING', $select_column_list, $select_column_list
#237: 'NOTIFY_SEARCH_SELECT_STRING', $select_str, $select_str
#267: 'NOTIFY_SEARCH_FROM_STRING', $from_str, $from_str
#333: 'NOTIFY_SEARCH_MATCHING_KEYWORD_FIELDS', '', $keyword_search_fields
#391: 'NOTIFY_SEARCH_WHERE_STRING', $this->searchOptions->keywords, $where_str, $keyword_search_fields
#452: 'NOTIFY_SEARCH_REAL_ORDERBY_STRING', $order_str, $order_str
#456: 'NOTIFY_SEARCH_ORDERBY_STRING', $listing_sql

```

#### includes/classes/payment.php
```
#61: 'NOTIFY_PAYMENT_CLASS_GET_INSTALLED_MODULES', $module
#120: 'NOTIFY_PAYMENT_MODULE_ENABLE'

```

#### includes/classes/Customer.php
```
#78: 'NOTIFY_CUSTOMER_IS_TAX_EXEMPT', [], $is_tax_exempt
#129: 'NOTIFY_ZEN_IS_CURRENTLY_LOGGED_IN', null, $is_currently_logged_in
#139: 'NOTIFY_ZEN_IS_LOGGED_IN', null, $is_logged_in
#177: //@TODO        'NOTIFY_?LOGIN_ATTEMPT', null, $is_logged_in
#236: 'NOTIFY_ZEN_IN_GUEST_CHECKOUT', null, $in_guest_checkout
#343: 'NOTIFY_CUSTOMER_DATA_LOADED', $this->data, $this->data
#437: 'NOTIFY_CUSTOMER_PRICING_GROUP_LOADED', $this->data
#466: 'NOTIFY_CUSTOMER_CHECK_IF_BANNED', $this->data, $banned_status
#475: 'NOTIFY_BAN_CUSTOMER', $this->data, $proceed_with_ban, $reset_shopping_session_and_basket
#839: 'NOTIFY_CUSTOMER_AFTER_RECORD_DELETED', (int)$this->customer_id
#848: 'NOTIFY_MODULE_CREATE_ACCOUNT_ADDING_CUSTOMER_RECORD', null, $data
#881: 'NOTIFY_MODULE_CREATE_ACCOUNT_ADDED_CUSTOMER_RECORD', array_merge(['customer_id' => $customer_id], $sql_data_array)
#918: 'NOTIFY_MODULE_CREATE_ACCOUNT_ADDED_ADDRESS_BOOK_RECORD', array_merge(['address_id' => $address_id], $sql_data_array)

```

#### includes/classes/order_total.php
```
#88: 'NOTIFY_ORDER_TOTAL_PROCESS_STARTS', ['order_info' => $order->info]
#96: 'NOTIFY_ORDER_TOTAL_PROCESS_NEXT', ['class' => $class, 'order_info' => $order->info, 'ot_output' => $GLOBALS[$class]->output]
#225: 'NOTIFY_ORDER_TOTAL_PRE_CONFIRMATION_CHECK_STARTS', ['order_info' => $orderInfoSaved]
#229: 'NOTIFY_ORDER_TOTAL_PRE_CONFIRMATION_CHECK_NEXT', ['class' => $class, 'order_info' => $order->info, 'ot_output' => $GLOBALS[$class]->output]

```

#### includes/classes/db/mysql/query_factory.php
```
#1061: 'NOTIFY_QUERY_FACTORY_META_DEFAULT', ['field' => $field, 'type' => $type], $this->max_length

```

#### includes/classes/CouponValidation.php
```
#36: 'NOTIFY_COUPON_ADDITIONAL_CHECKS', $product->fields, $coupon_id, $product_can_use_coupon

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

#### includes/classes/ajax/zcAjaxAdminSessionChange.php
```
#27: 'NOTIFY_AJAX_ADMIN_NOTIFICATIONS', '', $other_names

```

#### includes/init_includes/init_sanitize.php
```
#18: 'NOTIFY_INIT_SANITIZE_STARTS'
#23: 'NOTIFY_INIT_SANITIZE_GET_VAR_CHECK', ['name' => $varname, 'value' => $varvalue,], $get_var_override
#274: 'NOTIFY_INIT_SANITIZE_ENDS'

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

#### includes/init_includes/init_add_crumbs.php
```
#61: 'NOTIFY_INIT_ADD_CRUMBS_GET_TERMS_LINK_PARAMETERS', $next_get_term, $link_parameters

```

#### includes/index_filters/default_filter.php
```
#147: 'NOTIFY_PRODUCT_LISTING_QUERY_STRING', ['default'], $listing_sql, $where_str, $order_by

```

#### includes/index_filters/music_genre_filter.php
```
#143: 'NOTIFY_PRODUCT_LISTING_QUERY_STRING', ['music_genre'], $listing_sql, $where_str, $order_by

```

#### includes/index_filters/record_company_filter.php
```
#144: 'NOTIFY_PRODUCT_LISTING_QUERY_STRING', ['record_company'], $listing_sql, $where_str, $order_by

```

#### includes/functions/html_output.php
```
#17: 'NOTIFY_SEFU_INTERCEPT', array(), $link, $page, $parameters, $connection, $add_session_id, $static, $use_dir_ws_catalog
#215: 'NOTIFY_HANDLE_IMAGE', [$newimg]
#223: 'NOTIFY_OPTIMIZE_IMAGE', $template_dir, $src, $title, $width, $height, $parameters
#304: 'PAGE_OUTPUT_IMAGE_SUBMIT'
#328: 'PAGE_OUTPUT_IMAGE_BUTTON'
#360: 'NOTIFY_ZEN_DRAW_BUTTON', null, $text, $classes, $added_classes, $id, $parameters, $title, $type, $the_button
#438:  'NOTIFY_ZEN_CSS_BUTTON_SUBMIT', array( 'button_name' => $button_name, 'text' => $text, 'sec_class' => $sec_class, 'parameters' => $parameters, ), $css_button 
#459:  'NOTIFY_ZEN_CSS_BUTTON_BUTTON', array( 'button_name' => $button_name, 'text' => $text, 'sec_class' => $sec_class, 'parameters' => $parameters, ), $css_button 
#561:  'NOTIFY_ZEN_DRAW_INPUT_FIELD_OVERRIDE', array( 'name' => $name, 'value' => $value, 'parameters' => $parameters, 'type' => $type, 'reinsert_value' => $reinsert_value, 'required' => $required, ), $field 
#591:  'NOTIFY_ZEN_DRAW_INPUT_FIELD', array( 'name' => $name, 'value' => $value, 'parameters' => $parameters, 'type' => $type, 'reinsert_value' => $reinsert_value, 'required' => $required, ), $field 
#626:  'NOTIFY_ZEN_DRAW_SELECTION_FIELD_OVERRIDE', array( 'name' => $name, 'value' => $value, 'parameters' => $parameters, 'type' => $type, 'checked' => $checked ), $selection 
#661:  'NOTIFY_ZEN_DRAW_SELECTION_FIELD', array( 'name' => $name, 'value' => $value, 'parameters' => $parameters, 'type' => $type, 'checked' => $checked ), $selection 
#697:  'NOTIFY_ZEN_DRAW_TEXTAREA_FIELD_OVERRIDE', array( 'name' => $name, 'width' => $width, 'height' => $height, 'text' => $text, 'parameters' => $parameters, 'reinsert_value' => $reinsert_value, ), $field 
#730:  'NOTIFY_ZEN_DRAW_TEXTAREA_FIELD', array( 'name' => $name, 'width' => $width, 'height' => $height, 'text' => $text, 'parameters' => $parameters, 'reinsert_value' => $reinsert_value, ), $field 
#805:  'NOTIFY_ZEN_DRAW_PULL_DOWN_MENU_OVERRIDE', array( 'name' => $name, 'values' => $values, 'default' => $default, 'parameters' => $parameters, 'required' => $required, ), $field 
#854:  'NOTIFY_ZEN_DRAW_PULL_DOWN_MENU', array( 'name' => $name, 'values' => $values, 'default' => $default, 'parameters' => $parameters, 'required' => $required, ), $field 

```

#### includes/functions/functions_categories.php
```
#785: 'NOTIFY_GET_CATEGORY_DESCRIPTION', $category_id, $category->fields['categories_description']
#1104: 'NOTIFIER_ADMIN_ZEN_REMOVE_CATEGORY', array(), $category_id

```

#### includes/functions/functions_products.php
```
#66: 'NOTIFY_PRODUCT_INFO_PRODUCT_STATUS_CHECK', $product_info, $product_status, $should_throw_404, $response_code, $use_custom_response_code
#469:  'ZEN_GET_PRODUCTS_STOCK', $products_id, $products_quantity, $quantity_handled 
#499:  'ZEN_CHECK_STOCK_MESSAGE', [ $products_id, $products_quantity ], $out_of_stock_message 
#567: 'NOTIFY_GET_PRODUCTS_DESCRIPTION', $product_id, $data
#764: 'NOTIFIER_ADMIN_ZEN_REMOVE_PRODUCT', [], $product_id, $ptc
#857: 'NOTIFIER_ADMIN_ZEN_PRODUCTS_ATTRIBUTES_DOWNLOAD_DELETE', [], $product_id

```

#### includes/functions/functions_search.php
```
#163: 'NOTIFY_BUILD_KEYWORD_SEARCH', '', $fields, $string

```

#### includes/functions/functions_prices.php
```
#63: 'NOTIFY_ZEN_GET_PRODUCTS_SPECIAL_PRICE', $product->fields, $sale, $product_price
#202:  'NOTIFY_ZEN_GET_PRODUCTS_DISPLAY_PRICE_SALE', [ 'products_id' => $product_id, 'display_sale_price' => $display_sale_price, 'display_special_price' => $display_special_price, 'display_normal_price' => $display_normal_price, 'products_tax_class_id' => $product_check->fields['products_tax_class_id'] ], $pricing_handled, $show_sale_discount 
#264:  'NOTIFY_ZEN_GET_PRODUCTS_DISPLAY_PRICE_SPECIAL', [ 'products_id' => $product_id, 'display_sale_price' => $display_sale_price, 'display_special_price' => $display_special_price, 'display_normal_price' => $display_normal_price, 'products_tax_class_id' => $product_check->fields['products_tax_class_id'], 'product_is_free' => $product_check->fields['product_is_free'] ], $pricing_handled, $show_normal_price, $show_special_price, $show_sale_price 
#332:  'NOTIFY_ZEN_GET_PRODUCTS_DISPLAY_PRICE_NORMAL', [ 'products_id' => $product_id, 'display_sale_price' => $display_sale_price, 'display_special_price' => $display_special_price, 'display_normal_price' => $display_normal_price, 'products_tax_class_id' => $product_check->fields['products_tax_class_id'], 'product_is_free' => $product_check->fields['product_is_free'], 'display_wholesale_price' => $display_wholesale_price, 'has_wholesale_price' => $has_wholesale_price, ], $pricing_handled, $show_normal_price, $show_special_price, $show_sale_price 
#405:  'NOTIFY_ZEN_GET_PRODUCTS_DISPLAY_PRICE_FREE_OR_CALL', [ 'product_is_free' => $product_check->fields['product_is_free'], 'product_is_call' => $product_check->fields['product_is_call'], ], $tags_handled, $free_tag, $call_tag 
#454: 'ZEN_GET_PRODUCTS_BASE_PRICE', $product_id, $products_base_price, $base_price_is_handled

```

#### includes/functions/functions_traffic.php
```
#50: 'NOTIFY_ZEN_ADMIN_INVALID_IP_DETECTED', $original_ip
#52: 'NOTIFY_ZEN_INVALID_IP_DETECTED', $original_ip

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
#328:  'NOTIFY_END_ZEN_ADDRESS_FORMAT', [ 'format' => $fmt, 'address' => $incoming, 'firstname' => $address['$firstname'], 'lastname' => $address['$lastname'], 'street' => $address['$street'], 'suburb' => $address['$suburb'], 'city' => $address['$city'], 'state' => $address['$state'], 'country' => $address['$country'], 'postcode' => $address['$postcode'], 'company' => $address['$company'], 'streets' => $address['$streets'], 'statecomma' => $address['$statecomma'], 'zip' => $address['$zip'], 'cr' => $address['$cr'], 'hr' => $address['$hr'], ], $address_out 
#377: 'NOTIFY_ZEN_ADDRESS_LABEL', null, $customers_id, $address_id, $address->fields

```

#### includes/functions/functions_customers.php
```
#160: 'NOTIFY_ZEN_IN_GUEST_CHECKOUT', null, $in_guest_checkout
#172: 'NOTIFY_ZEN_IS_LOGGED_IN', null, $is_logged_in

```

#### includes/functions/functions_general.php
```
#191: 'NOTIFY_ZEN_SOLD_OUT_IMAGE', array_merge($button_check->fields, ['products_id' => (int)$product_id]), $return_button
#202: 'NOTIFY_ZEN_GET_BUY_NOW_BUTTON_RETURN', array_merge($button_check->fields, ['products_id' => (int)$product_id]), $return_button

```

#### includes/functions/functions_attributes.php
```
#29: 'NOTIFY_GET_ATTRIBUTE_DETAILS_BY_ID', [$attributes_id], $result
#57: 'NOTIFY_GET_ATTRIBUTE_DETAILS', [$products_id, $options_id, $options_values_id], $result
#79: 'NOTIFY_ZEN_HAS_PRODUCT_ATTRIBUTES_CHECK', ['products_id' => $product_id, 'not_readonly' => $not_readonly], $has_attributes
#123: 'NOTIFY_FUNCTIONS_LOOKUPS_REQUIRES_ATTRIBUTES_SELECTION_OTHER', ['products_id' => $products_id], $has_attributes
#148: 'NOTIFY_FUNCTIONS_LOOKUPS_REQUIRES_ATTRIBUTES_SELECTION', '', $query, $noSingles, $noDoubles
#209: 'FUNCTIONS_LOOKUPS_OPTION_NAME_NO_VALUES_OPT_TYPE', $opt_type, $test_var
#231: 'NOTIFY_ZEN_HAS_PRODUCT_ATTRIBUTES_VALUES', $product_id, $value_to_return
#478: 'ZEN_COPY_PRODUCTS_ATTRIBUTES_START', ['from' => $products_id_from, 'to' => $products_id_to]
#490: 'ZEN_COPY_PRODUCTS_ATTRIBUTES_DELETE', $products_id_to
#558: 'ZEN_COPY_PRODUCTS_ATTRIBUTES_ADD', ['pID' => $products_id_to, 'fields' => $copy_from]
#576: 'ZEN_COPY_PRODUCTS_ATTRIBUTES_ADDED_DOWNLOAD', $products_id_to, $new_products_attributes_id, $new_attribute_id
#617: 'ZEN_COPY_PRODUCTS_ATTRIBUTES_UPDATE', ['pID' => $products_id_to, 'fields' => $copy_from]
#622: 'ZEN_COPY_PRODUCTS_ATTRIBUTES_COMPLETE', ['from' => $products_id_from, 'to' => $products_id_to]
#663: 'NOTIFIER_ADMIN_ZEN_DELETE_PRODUCTS_ATTRIBUTES', [], $product_id
#776: 'NOTIFY_TEST_DOWNLOADABLE_FILE_EXISTS', $check_filename, $handler

```

#### includes/functions/functions_taxes.php
```
#30:  'NOTIFY_ZEN_GET_TAX_RATE_OVERRIDE', [ 'class_id' => $class_id, 'country_id' => $country_id, 'zone_id' => $zone_id ], $tax_rate 
#97:  'NOTIFY_ZEN_GET_TAX_DESCRIPTION_OVERRIDE', [ 'class_id' => $class_id, 'country_id' => $country_id, 'zone_id' => $zone_id ], $tax_description 
#162:  'NOTIFY_ZEN_GET_MULTIPLE_TAX_RATES_OVERRIDE', [ 'class_id' => $class_id, 'country_id' => $country_id, 'zone_id' => $zone_id, 'tax_description' => $tax_description ], $rates_array 
#353:  'ZEN_GET_TAX_LOCATIONS', [ 'country' => $store_country, 'zone' => $store_zone ], $tax_address 
#426:  'NOTIFY_ZEN_GET_ALL_TAX_DESCRIPTIONS_OVERRIDE', [ 'country_id' => $country_id, 'zone_id' => $zone_id ], $tax_descriptions 

```

#### includes/functions/functions_email.php
```
#110: 'NOTIFY_EMAIL_ADDRESS_TEST', [], $to_name, $to_email_address, $email_subject
#113: 'NOTIFY_EMAIL_ADDRESS_VALIDATION_FAILURE', sprintf(EMAIL_SEND_FAILED . ' (failed validation)', $to_name, $to_email_address, $email_subject)
#226: 'NOTIFY_EMAIL_DETERMINING_EMAIL_FORMAT', $to_email_address, $customers_email_format, $module
#248: 'NOTIFY_EMAIL_AFTER_EMAIL_FORMAT_DETERMINED'
#390: 'NOTIFY_EMAIL_BEFORE_PROCESS_ATTACHMENTS', ['attachments' => $attachments_list, 'module' => $module], $mail, $attachments_list
#422: 'NOTIFY_EMAIL_AFTER_PROCESS_ATTACHMENTS', count($attachments_list)
#467: 'NOTIFY_EMAIL_READY_TO_SEND', [$mail], $mail
#489: 'NOTIFY_EMAIL_AFTER_SEND'
#494: 'NOTIFY_EMAIL_AFTER_SEND_WITH_ALL_PARAMS', [$to_name, $to_email_address, $from_email_name, $from_email_address, $email_subject, $email_html, $text, $module, $ErrorInfo]
#520: 'NOTIFY_EMAIL_AFTER_SEND_ALL_SPECIFIED_ADDRESSES'
#544: 'NOTIFY_EMAIL_BEGIN_ARCHIVE_WRITE', [$to_name, $to_email_address, $from_email_name, $from_email_address, $email_subject, $email_html, $email_text, $module, $error_msgs]
#905: 'NOTIFY_EMAIL_VALIDATION_TEST', [$email, $valid_address]

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
#52: 'NOTIFY_HTML_HEAD_TAG_START', $current_page_base
#85: 'NOTIFY_HTML_HEAD_CSS_BEGIN', $current_page_base
#101: 'NOTIFY_HTML_HEAD_JS_BEGIN', $current_page_base
#141: 'NOTIFY_HTML_HEAD_END', $current_page_base

```

#### includes/templates/responsive_classic/common/tpl_main_page.php
```
#95: 'NOTIFY_PAGE_BODY_BEGIN', $current_page
#269: 'NOTIFY_FOOTER_END', $current_page

```

#### includes/templates/responsive_classic/common/tpl_tabular_display.php
```
#11: 'NOTIFY_TPL_TABULAR_DISPLAY_START', $current_page_base, $list_box_contents
#49: 'NOTIFY_TPL_TABULAR_DISPLAY_END', $current_page_base, $list_box_contents

```

#### includes/templates/responsive_classic/common/tpl_footer.php
```
#39: 'NOTIFY_FOOTER_AFTER_NAVSUPP', []

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
#37: 'NOTIFY_HTML_HEAD_TAG_START', $current_page_base
#69: 'NOTIFY_HTML_HEAD_CSS_BEGIN', $current_page_base
#81: 'NOTIFY_HTML_HEAD_JS_BEGIN', $current_page_base
#88: 'NOTIFY_HTML_HEAD_END', $current_page_base

```

#### includes/templates/template_default/common/tpl_main_page.php
```
#71: 'NOTIFY_PAGE_BODY_BEGIN', $current_page
#205: 'NOTIFY_FOOTER_END', $current_page

```

#### includes/templates/template_default/common/tpl_tabular_display.php
```
#11: 'NOTIFY_TPL_TABULAR_DISPLAY_START', $current_page_base, $list_box_contents
#50: 'NOTIFY_TPL_TABULAR_DISPLAY_END', $current_page_base, $list_box_contents

```

#### includes/templates/template_default/common/tpl_footer.php
```
#41: 'NOTIFY_FOOTER_AFTER_NAVSUPP', []

```

#### includes/templates/template_default/templates/tpl_account_history_info_default.php
```
#21: 'NOTIFY_ACCOUNT_HISTORY_INFO_EXTRA_COLUMN_HEADING', $order, $extra_headings
#49: 'NOTIFY_ACCOUNT_HISTORY_INFO_EXTRA_COLUMN_DATA', [ 'order' => $order, 'orders_product' => $op ], $extra_data
#116: 'NOTIFY_INVOICE_ADDITIONAL_DATA_MIDDLE', $order, $additional_content
#139: 'NOTIFY_ACCOUNT_HISTORY_INFO_OSH_HEADINGS', $order, $extra_headings
#161: 'NOTIFY_ACCOUNT_HISTORY_INFO_OSH_DATA', $statuses, $extra_data

```

#### includes/modules/featured_products.php
```
#75: 'NOTIFY_MODULES_FEATURED_PRODUCTS_B4_LIST_BOX', [], $data, $products_price

```

#### includes/modules/main_product_image.php
```
#16: 'NOTIFY_MODULES_MAIN_PRODUCT_IMAGE_START'
#38:  'NOTIFY_MODULES_MAIN_PRODUCT_IMAGE_FILENAME', $products_image, $main_image_handled, $products_image_extension, $products_image_base, $products_image_medium, $products_image_large 
#75: 'NOTIFY_MODULES_MAIN_PRODUCT_IMAGE_END'

```

#### includes/modules/specials_index.php
```
#79: 'NOTIFY_MODULES_SPECIALS_INDEX_B4_LIST_BOX', [], $data, $products_price

```

#### includes/modules/responsive_classic/ezpages_bar_header.php
```
#12: 'NOTIFY_START_EZPAGES_HEADERBAR'
#70: 'NOTIFY_END_EZPAGES_HEADERBAR'

```

#### includes/modules/responsive_classic/product_listing.php
```
#38: 'NOTIFY_MODULE_PRODUCT_LISTING_RESULTCOUNT', $listing_split->number_of_rows
#285: 'NOTIFY_MODULES_PRODUCT_LISTING_PRODUCTS_BUTTON', [], $record, $lc_button
#441: 'NOTIFY_PRODUCT_LISTING_END', $current_page_base, $list_box_contents, $listing_split, $show_top_submit_button, $show_bottom_submit_button, $show_submit, $how_many

```

#### includes/modules/hreflang.php
```
#25: 'NOTIFY_MODULE_START_HREFLANG', $current_page_base, $bypass, $lng, $languages, $canonicalLink

```

#### includes/modules/ezpages_mobile.php
```
#13: 'NOTIFY_START_EZPAGES_MOBILE'
#67: 'NOTIFY_END_EZPAGES_FOOTERBAR'

```

#### includes/modules/checkout_new_address.php
```
#10: 'NOTIFY_MODULE_START_CHECKOUT_NEW_ADDRESS'
#140: 'NOTIFY_MODULE_CHECKOUT_NEW_ADDRESS_VALIDATION', [], $error
#173: 'NOTIFY_MODULE_CHECKOUT_ADDED_ADDRESS_BOOK_RECORD', array_merge(['address_id' => $address_book_id], $sql_data_array)
#272: 'NOTIFY_MODULE_END_CHECKOUT_NEW_ADDRESS'

```

#### includes/modules/category_row.php
```
#41: 'NOTIFY_CATEGORY_ROW_IMAGE', $next_category['categories_id'], $next_category['categories_image']

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
#118: 'NOTIFY_ATTRIBUTES_MODULE_START_OPTION', $products_options_names->fields
#147: 'NOTIFY_ATTRIBUTES_MODULE_START_OPTIONS_LOOP', $i++, $products_options->fields, $products_options_names->fields, $data_properties, $field_disabled, $attributeDetailsArrayForJson
#203: 'NOTIFY_ATTRIBUTES_MODULE_SALEMAKER_DISPLAY_PRICE_PERCENTAGE', $products_options->fields, $product_info->fields, $products_options_display_price, $data_properties
#223: 'NOTIFY_ATTRIBUTES_MODULE_ORIGINAL_PRICE', $products_options->fields, $products_options_array, $products_options_display_price, $data_properties
#296: 'NOTIFY_ATTRIBUTES_MODULE_RADIO_SELECTED', $products_options->fields, $data_properties
#385: 'NOTIFY_ATTRIBUTES_MODULE_CHECKBOX_SELECTED', $products_options->fields, $data_properties
#521: 'NOTIFY_ATTRIBUTES_MODULE_FORMAT_VALUE', array_merge($products_options->fields, $products_options_names->fields), $data_properties, $field_disabled, $attributeDetailsArrayForJson
#561: 'NOTIFY_ATTRIBUTES_MODULE_BEFORE_ASSEMBLE_OUTPUTS', $products_options->fields, $data_properties, $inputFieldId, $field_disabled
#637: 'NOTIFY_ATTRIBUTES_MODULE_DEFAULT_SWITCH', $products_options_names->fields, $options_name, $options_menu, $options_comment, $options_comment_position, $options_html_id, $data_properties, $options_inputfield_id
#644: 'NOTIFY_ATTRIBUTES_MODULE_OPTION_BUILT', $products_options_names->fields, $options_name, $options_menu, $options_comment, $options_comment_position, $options_html_id, $options_attributes_image, $data_properties, $options_inputfield_id
#649: 'NOTIFY_ATTRIBUTES_MODULE_END', $prod_id, $options_name, $options_menu, $options_comment, $options_comment_position, $options_html_id, $options_attributes_image, $options_inputfield_id, $attributeDetailsArrayForJson

```

#### includes/modules/create_account.php
```
#10: 'NOTIFY_MODULE_START_CREATE_ACCOUNT'
#45: 'NOTIFY_CREATE_ACCOUNT_CAPTCHA_CHECK', $antiSpamFieldName, $antiSpam
#152: 'NOTIFY_CREATE_ACCOUNT_LOOKUP_BY_EMAIL', $email_address, $already_exists, $send_welcome_email
#159: 'NOTIFY_NICK_CHECK_FOR_EXISTING_EMAIL', $email_address, $nick_error, $nick
#167: 'NOTIFY_NICK_CHECK_FOR_MIN_LENGTH', $nick, $nick_error, $nick_length_min
#171: 'NOTIFY_NICK_CHECK_FOR_DUPLICATE', $nick, $nick_error
#262: 'NOTIFY_CREATE_ACCOUNT_VALIDATION_CHECK', [], $error, $send_welcome_email
#274: 'NOTIFY_FAILURE_DURING_CREATE_ACCOUNT'
#276: 'NOTIFY_SPAM_DETECTED_DURING_CREATE_ACCOUNT'
#301: 'NOTIFY_NICK_CREATE_NEW', $nick, $password, $nick_email, $extra_welcome_text
#304: 'NOTIFY_LOGIN_SUCCESS_VIA_CREATE_ACCOUNT', $email_address, $extra_welcome_text, $send_welcome_email
#419: 'NOTIFY_NICK_SET_TEMPLATE_FLAG', 0, $display_nick_field
#422: 'NOTIFY_MODULE_END_CREATE_ACCOUNT'

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
#463: 'NOTIFY_PAYPALWPP_BEFORE_DOEXPRESSCHECKOUT'
#520: 'NOTIFY_PAYPALWPP_BEFORE_PROCESS_FINISHED', $response
#588: 'NOTIFY_PAYPALWPP_AFTER_PROCESS_FINISHED', $paypal_order
#741: 'NOTIFY_PAYMENT_PAYPALWPP_INSTALLED'
#784: 'NOTIFY_PAYMENT_PAYPALWPP_UNINSTALLED'
#1320: 'NOTIFY_PAYMENT_PAYPALEC_SUBTOTALS_TAX', $order, $order_totals
#1413: 'NOTIFY_PAYPALWPP_GETLINEITEMDETAILS', $numberOfLineItemsProcessed, $optionsLI
#1763: 'NOTIFY_PAYMENT_PAYPALEC_BEFORE_SETEC', array(), $options, $order, $order_totals
#1771: 'NOTIFY_PAYMENT_PAYPALEC_TOKEN', $response, $options
#1888: 'NOTIFY_PAYPALEC_PARSE_GETEC_RESULT', array(), $response
#1926: 'NOTIFY_PAYPAL_EXPRESS_CHECKOUT_PAYERID_DETERMINED', $response['PAYERID']
#2066: 'NOTIFY_PAYPAL_CUSTOMER_ATTEMPT_TO_USE_INVALID_COUNTRY_CODE'
#2162: 'NOTIFY_PAYPALEXPRESS_BYPASS_ADDRESS_CREATION', $paypal_ec_payer_info, $bypass_address_creation
#2273: 'NOTIFY_PAYPALEXPRESS_CREATE_ACCOUNT_ADDED_CUSTOMER_RECORD', $customer_id, $sql_data_array
#2304: 'NOTIFY_PAYPALEXPRESS_CREATE_ACCOUNT_ADDED_ADDRESS_BOOK_RECORD', array(), $address_id, $sql_data_array
#2357: 'NOTIFY_LOGIN_SUCCESS_VIA_CREATE_ACCOUNT', 'paypal express checkout'
#2398: 'NOTIFY_PAYPALEC_END_ECSTEP2', $order
#2470: 'NOTIFY_PAYPALWPP_DISABLE_GET_OVERRIDE_ADDRESS', $address_id, $disable_address_override
#2731: 'NOTIFY_HEADER_ADDRESS_BOOK_ADD_ENTRY_INVALID_ATTEMPT', $customer_id, $country_id, $address_format_id, $address_question_arr
#2801: 'NOTIFY_HEADER_ADDRESS_BOOK_ADD_ENTRY_DONE', 'paypal express checkout', $new_address_book_id, $sql_data_array, $make_default
#3088: 'NOTIFY_PAYPALWPP_ERROR_HANDLER', $response, $operation, $basicError, $ignoreList, $errorInfo

```

#### includes/modules/payment/paypal/paypal_curl.php
```
#113: 'NOTIFY_PAYPAL_CURL_CONSTRUCT', $params
#160: 'NOTIFY_PAYPAL_SETEXPRESSCHECKOUT'
#176: 'NOTIFY_PAYPAL_GETEXPRESSCHECKOUTDETAILS'
#200: 'NOTIFY_PAYPAL_DOEXPRESSCHECKOUTPAYMENT'
#243: 'NOTIFY_PAYPAL_DODIRECTPAYMENT'
#565: 'NOTIFY_PAYPAL_CURL_BUILDNAMEVALUELIST', $string
#669: 'PAYPAL_CURL_LOG', $token, $tokenHash

```

#### includes/modules/payment/authorizenet_aim.php
```
#416: 'NOTIFY_PAYMENT_AUTHNET_EMULATOR_CHECK', $this->code, $submit_data
#431: 'NOTIFY_PAYMENT_AUTHNET_PRESUBMIT_HOOK', $this->code, $submit_data
#437: 'NOTIFY_PAYMENT_AUTHNET_POSTSUBMIT_HOOK', $this->code, $response
#622: 'NOTIFY_PAYMENT_AUTHNET_MODE_SELECTION', $this->mode, $submit_data
#702: 'NOTIFY_PAYMENT_AUTHNET_ENCAPSULATION_CHECK'

```

#### includes/modules/payment/paypal.php
```
#403: 'NOTIFY_PAYMENT_PAYPAL_RETURN_TO_STORE', $_GET
#428: 'NOTIFY_PAYMENT_PAYPAL_CANCELLED_DURING_CHECKOUT', $_GET
#579: 'NOTIFY_PAYMENT_PAYPAL_INSTALLED'
#588: 'NOTIFY_PAYMENT_PAYPAL_UNINSTALLED'

```

#### includes/modules/downloads.php
```
#107: 'NOTIFY_MODULE_DOWNLOAD_TEMPLATE_DETAILS', $data, $data

```

#### includes/modules/shipping/zones.php
```
#169: 'NOTIFY_SHIPPING_ZONES_UPDATE_STATUS', [], $this->enabled

```

#### includes/modules/shipping/flat.php
```
#68: 'NOTIFY_SHIPPING_FLAT_UPDATE_STATUS', [], $this->enabled

```

#### includes/modules/shipping/storepickup.php
```
#89: 'NOTIFY_SHIPPING_STOREPICKUP_UPDATE_STATUS', [], $this->enabled

```

#### includes/modules/shipping/freeoptions.php
```
#148: 'NOTIFY_SHIPPING_FREEOPTIONS_UPDATE_STATUS', [], $this->enabled

```

#### includes/modules/shipping/freeshipper.php
```
#69: 'NOTIFY_SHIPPING_FREESHIPPER_UPDATE_STATUS', [], $this->enabled

```

#### includes/modules/shipping/item.php
```
#69: 'NOTIFY_SHIPPING_ITEM_UPDATE_STATUS', [], $this->enabled

```

#### includes/modules/shipping/perweightunit.php
```
#90: 'NOTIFY_SHIPPING_PERWEIGHTUNIT_UPDATE_STATUS', [], $this->enabled

```

#### includes/modules/shipping/table.php
```
#89: 'NOTIFY_SHIPPING_TABLE_UPDATE_STATUS', [], $this->enabled

```

#### includes/modules/product_listing_alpha_sorter.php
```
#29: 'NOTIFY_PRODUCT_LISTING_ALPHA_SORTER_SELECTLIST', $prefix ?? '', $letters_list

```

#### includes/modules/additional_images.php
```
#15: 'NOTIFY_MODULES_ADDITIONAL_PRODUCT_IMAGES_START'
#67:  'NOTIFY_MODULES_ADDITIONAL_IMAGES_FILE_MATCH', [ 'file' => $file, 'file_extension' => $file_extension, 'products_image' => $products_image, 'products_image_base' => $products_image_base, ], $current_image_match 
#98: 'NOTIFY_MODULES_ADDITIONAL_PRODUCT_IMAGES_LIST', null, $images_array
#127: 'NOTIFY_MODULES_ADDITIONAL_IMAGES_GET_LARGE', $products_name, $products_image_large
#142: 'NOTIFY_MODULES_ADDITIONAL_IMAGES_THUMB_SLASHES', [], $thumb_slashes
#160:  'NOTIFY_MODULES_ADDITIONAL_IMAGES_SCRIPT_LINK', [ 'flag_display_large' => $flag_display_large, 'products_name' => $products_name, 'products_image_large' => $products_image_large, 'thumb_slashes' => $thumb_slashes, 'large_link' => $large_link, 'index' => $i, ], $script_link, $link_parameters 
#212: 'NOTIFY_MODULES_ADDITIONAL_PRODUCT_IMAGES_END'

```

#### includes/modules/checkout_address_book.php
```
#18: 'NOTIFY_MODULE_END_CHECKOUT_ADDRESS_BOOK', $customer, $addresses

```

#### includes/modules/sideboxes/information.php
```
#79: 'NOTIFY_INFORMATION_SIDEBOX_ADDITIONS', [], $information

```

#### includes/modules/sideboxes/ezpages.php
```
#10: 'NOTIFY_START_EZPAGES_SIDEBOX'
#68: 'NOTIFY_EZPAGES_SIDEBOX_ADDITIONS', [], $var_linksList
#72: 'NOTIFY_END_EZPAGES_SIDEBOX'
#77: 'NOTIFY_END_EZPAGES_SIDEBOX'

```

#### includes/modules/sideboxes/more_information.php
```
#31: 'NOTIFY_MORE_INFORMATION_SIDEBOX_ADDITIONS', [], $more_information

```

#### includes/modules/ezpages_bar_header.php
```
#12: 'NOTIFY_START_EZPAGES_HEADERBAR'
#70: 'NOTIFY_END_EZPAGES_HEADERBAR'

```

#### includes/modules/checkout_process.php
```
#12: 'NOTIFY_CHECKOUT_PROCESS_BEGIN'
#31: 'NOTIFY_CHECKOUT_SLAMMING_ALERT', $_SESSION['payment_attempt'], $slamming_threshold
#33: 'NOTIFY_CHECKOUT_SLAMMING_LOCKOUT'
#73: 'NOTIFY_CHECKOUT_PROCESS_BEFORE_ORDER_TOTALS_PRE_CONFIRMATION_CHECK'
#88: 'NOTIFY_CHECKOUT_PROCESS_BEFORE_ORDER_TOTALS_PROCESS'
#90: 'NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_TOTALS_PROCESS'
#105: 'NOTIFY_CHECKOUT_PROCESS_AFTER_PAYMENT_MODULES_BEFOREPROCESS'
#109: 'NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_CREATE', $insert_id
#111: 'NOTIFY_CHECKOUT_PROCESS_AFTER_PAYMENT_MODULES_AFTER_ORDER_CREATE', $insert_id
#115: 'NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_CREATE_ADD_PRODUCTS', $insert_id, $order
#118: 'NOTIFY_CHECKOUT_PROCESS_AFTER_SEND_ORDER_EMAIL', $insert_id, $order
#158: 'NOTIFY_CHECKOUT_PROCESS_HANDLE_AFFILIATES'

```

#### includes/modules/ezpages_bar_footer.php
```
#12: 'NOTIFY_START_EZPAGES_FOOTERBAR'
#69: 'NOTIFY_END_EZPAGES_FOOTERBAR'

```

#### includes/modules/product_listing.php
```
#38: 'NOTIFY_MODULE_PRODUCT_LISTING_RESULTCOUNT', $listing_split->number_of_rows
#278: 'NOTIFY_MODULES_PRODUCT_LISTING_PRODUCTS_BUTTON', [], $record, $lc_button
#427: 'NOTIFY_PRODUCT_LISTING_END', $current_page_base, $list_box_contents, $listing_split, $show_top_submit_button, $show_bottom_submit_button, $show_submit, $how_many

```

#### includes/modules/order_total/ot_shipping.php
```
#96:  'NOTIFY_OT_SHIPPING_TAX_CALCS', [], $external_shipping_tax_handler, $shipping_tax, $shipping_tax_description 

```

#### includes/modules/order_total/ot_group_pricing.php
```
#143: 'NOTIFY_OT_GROUP_PRICING_DEDUCTION_OVERRIDE', ['order_total' => $order_total], $od_amount
#191:  'NOTIFY_OT_GROUP_PRICING_DEDUCTION_OVERRIDE_FINAL', [ 'customers_group_pricing' => (int)$group_query->fields['customers_group_pricing'], 'group_percentage' => $group_discount->fields['group_percentage'], 'orderTotal' => $orderTotal, 'gift_vouchers' => $gift_vouchers, 'tax_calc_method' => $this->calculate_tax, 'order_info' => $order->info, ], $od_amount 

```

#### includes/modules/order_total/ot_coupon.php
```
#103: 'NOTIFY_OT_COUPON_START', true, $valid
#218: 'NOTIFY_OT_COUPON_CREDIT_SELECTION', true, $valid
#267: 'NOTIFY_OT_COUPON_GENERATE_POPUP_LINK', ['coupon_id' => $coupon_id, 'coupon_code' => $coupon_code], $couponLink
#371: 'NOTIFY_OT_COUPON_COUPON_INFO', ['coupon_result' => $coupon_details, 'code' => $coupon_code]
#623: 'NOTIFY_OT_COUPON_CALCS_FINISHED', ['coupon' => $coupon_details, 'order_totals' => $orderTotalDetails, 'od_amount' => $od_amount], $coupon_details
#653: 'NOTIFY_OT_COUPON_PRODUCT_VALIDITY', ['is_product_valid' => $is_product_valid, 'i' => $i]
#703: 'NOTIFY_OT_COUPON_ORDER_TOTAL_FINISHED', null, $return
#794: 'NOTIFY_OT_COUPON_COUPON_REMOVED'
#828: 'NOTIFY_COUPON_VALIDATION_PRODUCT_RESTRICTIONS', $coupon_id, $products, $found_valid
#1007: 'NOTIFY_OT_COUPON_USES_PER_USER_CHECK', $coupon_details, $valid
#1028: 'NOTIFY_OT_COUPON_USES_PER_CUSTOMER_GUEST_CHECKOUT_CHECK', $coupon_details, $valid

```

#### includes/modules/new_products.php
```
#83: 'NOTIFY_MODULES_NEW_PRODUCTS_B4_LIST_BOX', [], $new_products->fields, $products_price

```

#### includes/modules/pages/page/header_php.php
```
#19: 'NOTIFY_HEADER_START_EZPAGE'
#141: 'NOTIFY_HEADER_END_EZPAGE'

```

#### includes/modules/pages/checkout_success/header_php.php
```
#11: 'NOTIFY_HEADER_START_CHECKOUT_SUCCESS'
#197: 'NOTIFY_HEADER_END_CHECKOUT_SUCCESS'

```

#### includes/modules/pages/products_all/header_php.php
```
#11: 'NOTIFY_HEADER_START_PRODUCTS_ALL'
#52: 'NOTIFY_HEADER_END_PRODUCTS_ALL', null

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
#36: 'NOTIFY_PRODUCT_VIEWS_HIT_INCREMENTOR', (int)$_GET['products_id']
#111: 'NOTIFY_MAIN_TEMPLATE_VARS_PRODUCT_TYPE_VARS_PRODUCT_FREE_SHIPPING_INFO'
#140: 'NOTIFY_MAIN_TEMPLATE_VARS_EXTRA_PRODUCT_FREE_SHIPPING_INFO'
#148: 'NOTIFY_MAIN_TEMPLATE_VARS_END_PRODUCT_FREE_SHIPPING_INFO'

```

#### includes/modules/pages/product_free_shipping_info/header_php.php
```
#11: 'NOTIFY_HEADER_START_PRODUCT_FREE_SHIPPING_INFO'
#28: 'NOTIFY_HEADER_END_PRODUCT_FREE_SHIPPING_INFO'

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
#125: 'NOTIFY_HEADER_END_CHECKOUT_PAYMENT'

```

#### includes/modules/pages/document_general_info/main_template_vars.php
```
#14: 'NOTIFY_MAIN_TEMPLATE_VARS_START_DOCUMENT_GENERAL_INFO'
#36: 'NOTIFY_PRODUCT_VIEWS_HIT_INCREMENTOR', (int)$_GET['products_id']
#111: 'NOTIFY_MAIN_TEMPLATE_VARS_PRODUCT_TYPE_VARS_DOCUMENT_GENERAL_INFO'
#140: 'NOTIFY_MAIN_TEMPLATE_VARS_EXTRA_DOCUMENT_GENERAL_INFO'
#148: 'NOTIFY_MAIN_TEMPLATE_VARS_END_DOCUMENT_GENERAL_INFO'

```

#### includes/modules/pages/document_general_info/header_php.php
```
#11: 'NOTIFY_HEADER_START_DOCUMENT_GENERAL_INFO'
#23: 'NOTIFY_HEADER_END_DOCUMENT_GENERAL_INFO'

```

#### includes/modules/pages/document_general_info/main_template_vars_product_type.php
```
#17: 'NOTIFY_PRODUCT_TYPE_VARS_START_DOCUMENT_GENERAL_INFO'
#35: 'NOTIFY_PRODUCT_TYPE_VARS_END_DOCUMENT_GENERAL_INFO'

```

#### includes/modules/pages/checkout_confirmation/header_php.php
```
#11: 'NOTIFY_HEADER_START_CHECKOUT_CONFIRMATION'
#174: 'NOTIFY_HEADER_END_CHECKOUT_CONFIRMATION'

```

#### includes/modules/pages/product_reviews/header_php.php
```
#11: 'NOTIFY_HEADER_START_PRODUCT_REVIEWS'
#91: 'NOTIFY_HEADER_END_PRODUCT_REVIEWS'

```

#### includes/modules/pages/search_result/header_php.php
```
#16: 'NOTIFY_HEADER_START_ADVANCED_SEARCH_RESULTS'
#47: 'NOTIFY_SEARCH_RESULTS', $listing_sql, $keywords, $result
#55: 'NOTIFY_SEARCH_NO_RESULTS_MESSAGE', $result, $search, $message
#74: 'NOTIFY_HEADER_END_ADVANCED_SEARCH_RESULTS', $keywords

```

#### includes/modules/pages/brands/header_php.php
```
#10: 'NOTIFY_HEADER_START_BRANDS'
#65: 'NOTIFY_HEADER_END_BRANDS'

```

#### includes/modules/pages/contact_us/header_php.php
```
#11: 'NOTIFY_HEADER_START_CONTACT_US'
#30: 'NOTIFY_CONTACT_US_CAPTCHA_CHECK', $_POST
#37: 'NOTIFY_SPAM_DETECTED_USING_CONTACT_US', $_POST
#57: 'NOTIFY_CONTACT_US_ACTION', $_SESSION['customer_id'] ?? 0, $customer_email, $customer_name, $email_address, $name, $enquiry, $telephone
#158: 'NOTIFY_HEADER_END_CONTACT_US'

```

#### includes/modules/pages/featured_products/header_php.php
```
#11: 'NOTIFY_HEADER_START_FEATURED_PRODUCTS'
#52: 'NOTIFY_HEADER_END_FEATURED_PRODUCTS', null

```

#### includes/modules/pages/gv_send/header_php.php
```
#14: 'NOTIFY_HEADER_START_GV_SEND'
#214: 'NOTIFY_HEADER_END_GV_SEND'

```

#### includes/modules/pages/specials/header_php.php
```
#10: 'NOTIFY_HEADER_START_SPECIALS'
#81: 'NOTIFY_HEADER_END_SPECIALS', null

```

#### includes/modules/pages/checkout_shipping/header_php.php
```
#10: 'NOTIFY_HEADER_START_CHECKOUT_SHIPPING'
#229: 'NOTIFY_HEADER_END_CHECKOUT_SHIPPING'

```

#### includes/modules/pages/ask_a_question/header_php.php
```
#9: 'NOTIFY_HEADER_START_ASK_A_QUESTION'
#29: 'NOTIFY_ASK_A_QUESTION_ALLOW_BYPASS_REDIRECT', ['products_id' => $pid, ], $bypass_redirect
#81: 'NOTIFY_ASK_A_QUESTION_CAPTCHA_CHECK', $_POST
#88: 'NOTIFY_SPAM_DETECTED_USING_CONTACT_US', $_POST
#108: 'NOTIFY_ASK_A_QUESTION_ACTION', (isset($_SESSION['customer_id']) ? $_SESSION['customer_id'] : 0), $customer_email, $customer_name, $email_address, $name, $enquiry, $telephone
#205: 'NOTIFY_HEADER_END_ASK_A_QUESTION'

```

#### includes/modules/pages/page_not_found/header_php.php
```
#11: 'NOTIFY_HEADER_START_PAGE_NOT_FOUND'
#27: 'NOTIFY_HEADER_END_PAGE_NOT_FOUND'

```

#### includes/modules/pages/password_forgotten/header_php.php
```
#11: 'NOTIFY_HEADER_START_PASSWORD_FORGOTTEN'
#49: 'NOTIFY_PASSWORD_FORGOTTEN_VALIDATED', $email_address, $sessionMessage
#71: 'NOTIFY_PASSWORD_FORGOTTEN_CHANGED', $email_address, $check_customer->fields['customers_id'], $new_password
#74: 'NOTIFY_PASSWORD_FORGOTTEN_NOT_FOUND', $email_address, $sessionMessage
#86: 'NOTIFY_HEADER_END_PASSWORD_FORGOTTEN'

```

#### includes/modules/pages/unsubscribe/header_php.php
```
#11: 'NOTIFY_HEADER_START_UNSUBSCRIBE'
#60: 'NOTIFY_HEADER_END_UNSUBSCRIBE'

```

#### includes/modules/pages/order_status/header_php.php
```
#8: 'NOTIFY_HEADER_START_ORDER_STATUS'
#77: 'NOTIFY_ORDER_STATUS_SPAM_DETECTED'
#86: 'NOTIFY_ORDER_STATUS_VALIDATION_CHECK', '', $error
#94: 'NOTIFY_ORDER_STATUS_SLAMMING_ALERT', $_SESSION['os_errors'], $slamming_threshold
#96: 'NOTIFY_ORDER_STATUS_SLAMMING_LOCKOUT'
#150: 'NOTIFY_ORDER_STATUS_EXTRA_VALIDATION', '', $extra_validation_html
#155: 'NOTIFY_HEADER_END_ORDER_STATUS'

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
#55: 'NOTIFY_HEADER_END_POPUP_IMAGES_ADDITIONAL'

```

#### includes/modules/pages/document_product_info/main_template_vars.php
```
#14: 'NOTIFY_MAIN_TEMPLATE_VARS_START_DOCUMENT_PRODUCT_INFO'
#36: 'NOTIFY_PRODUCT_VIEWS_HIT_INCREMENTOR', (int)$_GET['products_id']
#111: 'NOTIFY_MAIN_TEMPLATE_VARS_PRODUCT_TYPE_VARS_DOCUMENT_PRODUCT_INFO'
#139: 'NOTIFY_MAIN_TEMPLATE_VARS_EXTRA_DOCUMENT_PRODUCT_INFO'
#147: 'NOTIFY_MAIN_TEMPLATE_VARS_END_DOCUMENT_PRODUCT_INFO'

```

#### includes/modules/pages/document_product_info/header_php.php
```
#11: 'NOTIFY_HEADER_START_DOCUMENT_PRODUCT_INFO'
#28: 'NOTIFY_HEADER_END_DOCUMENT_PRODUCT_INFO'

```

#### includes/modules/pages/document_product_info/main_template_vars_product_type.php
```
#17: 'NOTIFY_PRODUCT_TYPE_VARS_START_DOCUMENT_PRODUCT_INFO'
#35: 'NOTIFY_PRODUCT_TYPE_VARS_END_DOCUMENT_PRODUCT_INFO'

```

#### includes/modules/pages/gv_redeem/header_php.php
```
#15: 'NOTIFY_HEADER_START_GV_REDEEM'

```

#### includes/modules/pages/popup_image/header_php.php
```
#14: 'NOTIFY_HEADER_START_POPUP_IMAGES'
#70: 'NOTIFY_HEADER_END_POPUP_IMAGES'

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
#45: 'NOTIFY_HEADER_END_CHECKOUT_PAYMENT_ADDRESS'

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
#36: 'NOTIFY_PRODUCT_VIEWS_HIT_INCREMENTOR', (int)$_GET['products_id']
#111: 'NOTIFY_MAIN_TEMPLATE_VARS_PRODUCT_TYPE_VARS_PRODUCT_MUSIC_INFO'
#144: 'NOTIFY_MAIN_TEMPLATE_VARS_EXTRA_PRODUCT_MUSIC_INFO'
#152: 'NOTIFY_MAIN_TEMPLATE_VARS_END_PRODUCT_MUSIC_INFO'

```

#### includes/modules/pages/product_music_info/header_php.php
```
#11: 'NOTIFY_HEADER_START_PRODUCT_MUSIC_INFO'
#28: 'NOTIFY_HEADER_END_PRODUCT_MUSIC_INFO'

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
#35: 'NOTIFY_BEFORE_REDIRECT_ACTION_PRODUCT', [], $_GET['products_id'], $_SESSION['languages_id']
#43: 'NOTIFY_BEFORE_REDIRECT_ACTION_PRODUCT', [], $_GET['products_id'], $default_language_id
#57: 'NOTIFY_BEFORE_REDIRECT_ACTION_MUSIC_ARTIST', [], $_GET['artists_id'], $_SESSION['languages_id']
#66: 'NOTIFY_BEFORE_REDIRECT_ACTION_MUSIC_ARTIST', [], $_GET['artists_id'], $default_language_id
#81: 'NOTIFY_BEFORE_REDIRECT_ACTION_RECORD_COMPANY', [], $_GET['record_company_id'], $_SESSION['languages_id']
#90: 'NOTIFY_BEFORE_REDIRECT_ACTION_RECORD_COMPANY', [], $_GET['record_company_id'], $default_language_id
#104:  'NOTIFY_BEFORE_REDIRECT_ACTION_BANNER', [ 'banners_id' => (int)$_GET['goto'], 'banners_url' => $banner->fields['banners_url'], ] 
#124:  'NOTIFY_BEFORE_REDIRECT_ACTION_MANUFACTURER', [ 'manufacturers_id' => $_GET['manufacturers_id'], 'manufacturers_url' => $manufacturer->fields['manufacturers_url'], 'language_id' => $_SESSION['languages_id'], ] 
#150:  'NOTIFY_BEFORE_REDIRECT_ACTION_MANUFACTURER', [ 'manufacturers_id' => $_GET['manufacturers_id'], 'manufacturers_url' => $manufacturer->fields['manufacturers_url'], 'language_id' => $default_language_id, ] 
#175: 'NOTIFY_REDIRECT_DEFAULT_ACTION', $default_language_id

```

#### includes/modules/pages/index/main_template_vars.php
```
#11: 'NOTIFY_HEADER_START_INDEX_MAIN_TEMPLATE_VARS'
#54: 'NOTIFY_HEADER_INDEX_MAIN_TEMPLATE_VARS_RELEASE_PRODUCT_TYPE_VARS'
#229: 'NOTIFY_HEADER_INDEX_MAIN_TEMPLATE_VARS_PAGE_BODY', NULL, $tpl_page_body, $current_categories_name, $current_categories_description
#234: 'NOTIFY_HEADER_END_INDEX_MAIN_TEMPLATE_VARS', NULL, $current_categories_description

```

#### includes/modules/pages/index/header_php.php
```
#11: 'NOTIFY_HEADER_START_INDEX'
#63:  'NOTIFY_INDEX_CATEGORY_STATUS_CHECK', ['cPath' => $cPath, 'current_category_id' => $current_category_id], $category_redirect_handled, $current_category_not_found, $current_category_is_disabled, $current_category_has_products, $current_category_has_subcats, $category_depth 
#144: 'NOTIFY_HEADER_END_INDEX'

```

#### includes/modules/pages/product_info/main_template_vars.php
```
#14: 'NOTIFY_MAIN_TEMPLATE_VARS_START_PRODUCT_INFO'
#36: 'NOTIFY_PRODUCT_VIEWS_HIT_INCREMENTOR', (int)$_GET['products_id']
#111: 'NOTIFY_MAIN_TEMPLATE_VARS_PRODUCT_TYPE_VARS_PRODUCT_INFO'
#139: 'NOTIFY_MAIN_TEMPLATE_VARS_EXTRA_PRODUCT_INFO'
#145: 'NOTIFY_MAIN_TEMPLATE_VARS_END_PRODUCT_INFO'

```

#### includes/modules/pages/product_info/header_php.php
```
#11: 'NOTIFY_HEADER_START_PRODUCT_INFO'
#28: 'NOTIFY_HEADER_END_PRODUCT_INFO'

```

#### includes/modules/pages/product_info/main_template_vars_product_type.php
```
#17: 'NOTIFY_PRODUCT_TYPE_VARS_START_PRODUCT_INFO'
#35: 'NOTIFY_PRODUCT_TYPE_VARS_END_PRODUCT_INFO'

```

#### includes/modules/pages/gv_faq/header_php.php
```
#11: 'NOTIFY_HEADER_START_GV_FAQ'
#37: 'NOTIFY_HEADER_END_GV_FAQ'

```

#### includes/modules/pages/featured_categories/header_php.php
```
#12: 'NOTIFY_HEADER_START_FEATURED_CATEGORIES'
#47: 'NOTIFY_HEADER_END_FEATURED_CATEGORIES', null

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
#29: 'NOTIFY_HEADER_END_ACCOUNT'

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
#57: 'NOTIFY_HEADER_END_CHECKOUT_SHIPPING_ADDRESS'

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

#### includes/modules/pages/products_new/header_php.php
```
#11: 'NOTIFY_HEADER_START_PRODUCTS_NEW'
#57: 'NOTIFY_HEADER_END_PRODUCTS_NEW', null

```

#### includes/modules/pages/account_edit/header_php.php
```
#10: 'NOTIFY_HEADER_START_ACCOUNT_EDIT'
#90: 'NOTIFY_NICK_CHECK_FOR_EXISTING_EMAIL', $email_address, $nick_error, $nick
#99: 'NOTIFY_HEADER_ACCOUNT_EDIT_VERIFY_COMPLETE'
#103: 'NOTIFY_NICK_UPDATE_EMAIL_ADDRESS', $nick, $email_address
#148: 'NOTIFY_HEADER_ACCOUNT_EDIT_UPDATES_COMPLETE'
#202: 'NOTIFY_HEADER_END_ACCOUNT_EDIT'

```

#### includes/modules/pages/site_map/header_php.php
```
#11: 'NOTIFY_HEADER_START_SITE_MAP'
#25: 'NOTIFY_HEADER_END_SITE_MAP'

```

#### includes/modules/pages/login/header_php.php
```
#10: 'NOTIFY_HEADER_START_LOGIN'
#71: 'NOTIFY_LOGIN_BANNED'
#87: 'NOTIFY_PROCESS_3RD_PARTY_LOGINS', $email_address, $password, $loginAuthorized
#107: 'NOTIFY_LOGIN_SUCCESS'
#141: 'NOTIFY_LOGIN_FAILURE'
#153: 'NOTIFY_HEADER_END_LOGIN'

```

#### includes/modules/pages/checkout_process/header_php.php
```
#10: 'NOTIFY_HEADER_START_CHECKOUT_PROCESS'
#17: 'NOTIFY_CHECKOUT_PROCESS_BEFORE_CART_RESET', $insert_id
#25: 'NOTIFY_HEADER_END_CHECKOUT_PROCESS', $insert_id

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

#### includes/modules/product_prev_next.php
```
#14: 'NOTIFY_PRODUCT_PREV_NEXT_OVERRIDE', [], $prev_next_override

```

#### admin/packingslip.php
```
#62: 'NOTIFY_ADMIN_ORDERS_PACKINGSLIP_ADDITIONAL_DATA_TOP', $oID, $additional_content
#160: 'NOTIFY_ADMIN_PACKINGSLIP_HEADING', '', $extra_headings
#180: 'NOTIFY_ADMIN_PACKINGSLIP_SORT_DISPLAY', $order->products, $sort_order
#254: 'NOTIFY_ADMIN_PACKINGSLIP_DATA',  $order->products[$i]['id'], $extra_data
#328: 'NOTIFY_ADMIN_ORDERS_PACKINGSLIP_ADDITIONAL_DATA_BOTTOM', $oID, $additional_content

```

#### admin/attributes_controller.php
```
#337: 'NOTIFY_ATTRIBUTE_CONTROLLER_ADD_PRODUCT_ATTRIBUTES', $products_attributes_id
#485: 'NOTIFY_ATTRIBUTE_CONTROLLER_UPDATE_PRODUCT_ATTRIBUTE', $attribute_id
#498: 'NOTIFY_ATTRIBUTE_CONTROLLER_DELETE_ATTRIBUTE', ['attribute_id' => $attribute_id], $attribute_id
#515: 'NOTIFY_ATTRIBUTE_CONTROLLER_DELETE_ALL', ['pID' => $_POST['products_filter']]
#529: 'NOTIFY_ATTRIBUTE_CONTROLLER_DELETE_OPTION_NAME_VALUES', ['pID' => $_POST['products_filter'], 'options_id' => $_POST['products_options_id_all']]
#696: 'NOTIFY_ATTRIBUTE_CONTROLLER_ADDITIONAL_ACTIONS_DROPDOWN_UPPER', $zc_products, $action, $products_filter, $current_category_id, $additional_actions
#711: 'NOTIFY_ATTRIBUTE_CONTROLLER_ADDITIONAL_ACTIONS_DROPDOWN_SUBMENU', $zc_products, $action, $products_filter, $current_category_id, $additional_actions
#1341: 'NOTIFY_ADMIN_PRODUCT_ATTRIBUTES_COLLECT_INFO_EXTRA_INPUTS', $attributes_value, $extra_attributes_inputs
#1961: 'NOTIFY_ADMIN_PRODUCT_ATTRIBUTES_COLLECT_INFO_EXTRA_INPUTS', $attributes_value, $extra_attributes_inputs

```

#### admin/product.php
```
#29: 'NOTIFY_BEGIN_ADMIN_PRODUCTS', $action, $action

```

#### admin/languages.php
```
#179: 'NOTIFY_ADMIN_LANGUAGE_INSERT', (int)$insert_id
#255: 'NOTIFY_ADMIN_LANGUAGE_DELETE', (int)$lID

```

#### admin/category_product_listing.php
```
#291: 'NOTIFY_ADMIN_PROD_LISTING_DEFAULT_ACTION', $action, $clearAction
#580: 'NOTIFY_ADMIN_PROD_LISTING_HEADERS_B4_QTY', '', $extra_headings
#622:  'NOTIFY_ADMIN_CATEGORY_LISTING_HEADERS', [ 'categories' => $categories, 'categories_sql' => $sql, 'showing_products' => $show_prod_labels, ], $extra_headings 
#660: 'NOTIFY_ADMIN_PROD_LISTING_HEADERS_AFTER_QTY', '', $extra_headings
#741: 'NOTIFY_ADMIN_CATEGORY_LISTING_DATA', $category, $extra_data
#782: 'NOTIFY_ADMIN_PROD_LISTING_ADD_ICON_CATEGORY', $category, $additional_icons
#802:  'NOTIFY_ADMIN_PROD_LISTING_ADD_ACTION_ICONS', [ 'category' => ($category ?? null), 'product' => ($product ?? null), 'cPath' => ($cPath ?? null), 'current_category_id' => $current_category_id ], $extra_action_buttons 
#874: 'NOTIFY_ADMIN_PROD_LISTING_PRODUCTS_QUERY', '', $extra_select, $extra_from, $extra_joins, $extra_ands, $order_by, $extra_search_fields
#976: 'NOTIFY_ADMIN_PROD_LISTING_DATA_B4_QTY', $product, $extra_data
#1007: 'NOTIFY_ADMIN_PROD_LISTING_DATA_AFTER_QTY', $product, $extra_data
#1020: 'NOTIFY_ADMIN_PROD_LISTING_ADD_ICON', $product, $additional_icons
#1241: 'NOTIFY_ADMIN_PROD_LISTING_DEFAULT_INFOBOX', $action, $heading, $contents
#1266: 'NOTIFY_ADMIN_PROD_LISTING_SKIP_ACTIONS', $current_category_id, $zc_skip_products, $zc_skip_categories, $messageSubCategories

```

#### admin/admin_activity.php
```
#309: 'NOTIFY_ADMIN_ACTIVITY_LOG_RESET'

```

#### admin/includes/classes/class.admin.zcObserverLogEventListener.php
```
#59: $this->notifier->notify('NOTIFY_ADMIN_FIRE_LOG_WRITERS', $log_data
#176: $this->notifier->notify('NOTIFY_ADMIN_FIRE_LOG_WRITER_RESET'
#192: 'NOTIFY_ADMIN_ACTIVITY_LOG_EVENT', $message, $severity

```

#### admin/includes/init_includes/init_sanitize.php
```
#270: 'NOTIFY_ADMIN_CONFIGURATION_SPECIAL_CHARACTERS', [], $extra_configs_with_special_characters

```

#### admin/includes/init_includes/init_languages.php
```
#20: 'NOTIFY_LANGUAGE_CHANGE_REQUESTED_BY_ADMIN_VISITOR', $_GET['language'], $lng

```

#### admin/includes/init_includes/init_admin_history.php
```
#11: 'NOTIFY_ADMIN_ACTIVITY_LOG_EVENT', 'POST'

```

#### admin/includes/init_includes/init_admin_auth.php
```
#80: 'NOTIFY_ADMIN_NONSUPERUSER_ACTION'

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
#172: 'NOTIFIER_PLUGIN_HELP_PAGE_URL_LOOKUP', $page, $help_page

```

#### admin/includes/functions/admin_access.php
```
#439: 'NOTIFY_ADMIN_LOGIN_DENY', $admin_name, $error, $message

```

#### admin/includes/functions/general.php
```
#391: 'NOTIFIER_ADMIN_ZEN_REMOVE_ORDER', array(), $order_id, $restock

```

#### admin/includes/modules/new_product_preview.php
```
#23: 'NOTIFY_ADMIN_PRODUCT_IMAGE_UPLOADED', $products_image, $products_image_name

```

#### admin/includes/modules/update_product.php
```
#36: 'NOTIFY_MODULES_UPDATE_PRODUCT_START', ['action' => $action, 'products_id' => $products_id]
#124: 'NOTIFY_ADMIN_UPDATE_PRODUCT_UPDATE', $products_id, $sql_data_array
#154: 'NOTIFY_MODULES_UPDATE_PRODUCT_END', ['action' => $action, 'products_id' => $products_id]

```

#### admin/includes/modules/product_free_shipping/collect_info.php
```
#221: 'NOTIFY_ADMIN_PRODUCT_COLLECT_INFO_EXTRA_INPUTS', $pInfo, $extra_product_inputs

```

#### admin/includes/modules/document_general/collect_info.php
```
#235: 'NOTIFY_ADMIN_PRODUCT_COLLECT_INFO_EXTRA_INPUTS', $pInfo, $extra_product_inputs

```

#### admin/includes/modules/collect_info.php
```
#222: 'NOTIFY_ADMIN_PRODUCT_COLLECT_INFO_EXTRA_INPUTS', $pInfo, $extra_product_inputs
#277: 'NOTIFY_ADMIN_PRODUCT_PRICE_EDIT_SECTION_TOP', $pInfo, $additional_fields
#317: 'NOTIFY_ADMIN_PRODUCT_PRICE_EDIT_ABOVE', $pInfo, $additional_fields
#371: 'NOTIFY_ADMIN_PRODUCT_PRICE_EDIT_BELOW', $pInfo, $additional_fields

```

#### admin/includes/modules/search_box.php
```
#63: 'NOTIFY_ADMIN_SEARCH_BOX_FORM_GROUP', '', $extra_form_group

```

#### admin/includes/modules/document_product/collect_info.php
```
#221: 'NOTIFY_ADMIN_PRODUCT_COLLECT_INFO_EXTRA_INPUTS', $pInfo, $extra_product_inputs

```

#### admin/includes/modules/delete_product.php
```
#35: 'NOTIFY_ADMIN_DELETE_PRODUCT_INFOBOX', $pInfo, $product_master_category_string, $product_categories_string

```

#### admin/includes/modules/copy_product_confirm.php
```
#76: 'NOTIFY_MODULES_COPY_PRODUCT_CONFIRM_DUPLICATE_FIELDS', $product, $separately_updated_fields, $casted_fields
#243: 'NOTIFY_MODULES_COPY_TO_CONFIRM_DUPLICATE', compact('products_id', 'dup_products_id')

```

#### admin/includes/modules/product_music/collect_info.php
```
#268: 'NOTIFY_ADMIN_PRODUCT_COLLECT_INFO_EXTRA_INPUTS', $pInfo, $extra_product_inputs

```

#### admin/includes/modules/copy_product.php
```
#68: 'NOTIFY_ADMIN_PRODUCT_COPY_TO_ATTRIBUTES', $pInfo, $contents

```

#### admin/home.php
```
#40: 'NOTIFY_ADMIN_FOOTER_END'

```

#### admin/options_values_manager.php
```
#162: 'OPTIONS_VALUES_MANAGER_DELETE_VALUE', ['value_id' => $value_id]
#543:  'OPTIONS_VALUES_MANAGER_DELETE_VALUES_OF_OPTIONNAME', [ 'current_products_id' => $current_products_id, 'remove_ids' => $remove_downloads_ids, 'options_id' => $options_id_from, 'options_values_id' => $options_values_values_id_from ] 

```

#### admin/manufacturers.php
```
#31: 'NOTIFY_ADMIN_MANUFACTURERS_INSERT_UPDATE', ['action' => $action, 'manufacturers_id' => $manufacturers_id ?? 0], $sql_data_array
#141: 'NOTIFY_ADMIN_MANUFACTURERS_DEFAULT_ACTION', ['action' => $action]
#190: 'NOTIFY_ADMIN_MANUFACTURERS_EXTRA_COLUMN_HEADING', [], $extra_headings
#264: 'NOTIFY_ADMIN_MANUFACTURERS_EXTRA_COLUMN_DATA', $manufacturer, $extra_data
#325: 'NOTIFY_ADMIN_MANUFACTURERS_NEW', '', $additional_contents
#371: 'NOTIFY_ADMIN_MANUFACTURERS_EDIT', $mInfo, $additional_contents

```

#### admin/invoice.php
```
#67: 'NOTIFY_ADMIN_ORDERS_INVOICE_ADDITIONAL_DATA_TOP', $oID, $additional_content
#165: 'NOTIFY_ADMIN_INVOICE_HEADING_B4_TAX', '', $extra_headings
#206: 'NOTIFY_ADMIN_INVOIVE_HEADERS_AFTER_TAX', '', $extra_headings
#227: 'NOTIFY_ADMIN_INVOICE_SORT_DISPLAY', $order->products, $sort_order
#312: 'NOTIFY_ADMIN_INVOICE_DATA_B4_TAX',  $order->products[$i]['id'], $extra_data
#368: 'NOTIFY_ADMIN_INVOICE_DATA_AFTER_TAX', $order->products[$i]['id'], $extra_data
#386: 'NOTIFY_ADMIN_ORDERS_INVOICE_ADDITIONAL_DATA_MIDDLE', $oID, $additional_content
#469: 'NOTIFY_ADMIN_ORDERS_INVOICE_ADDITIONAL_DATA_BOTTOM', $oID, $additional_content

```

#### admin/whos_online.php
```
#206: 'ADMIN_WHOSONLINE_IP_LINKS', $item, $additional_ipaddress_links, $whois_url

```

#### admin/ezpages.php
```
#103: 'NOTIFY_ADMIN_EZPAGES_UPDATE_BASE', $action, $page_error, $sql_data_array
#138: 'NOTIFY_ADMIN_EZPAGES_UPDATE_LANG_INSERT', ['pages_id' => (int)$pages_id, 'languages_id' => $language_id], $sql_data_array
#155: 'NOTIFY_ADMIN_EZPAGES_UPDATE_LANG_UPDATE', ['pages_id' => (int)$pages_id, 'languages_id' => $language_id], $sql_data_array
#273: 'NOTIFY_ADMIN_EZPAGES_NEW', '', $parameters
#349: 'NOTIFY_ADMIN_EZPAGES_FORM_FIELDS', $ezInfo, $extra_page_inputs
#530: 'NOTIFY_ADMIN_EZPAGES_MENU_LEGEND', [], $extra_legends
#775: 'NOTIFY_ADMIN_EZPAGES_EXTRA_ACTION_ICONS', $page, $extra_action_icons

```

#### admin/coupon_admin.php
```
#114: 'ADMIN_COUPON_CODE_EMAILED_TO_CUSTOMER', $coupon_result->fields['coupon_code'], $item['customers_email_address']

```

#### admin/index_dashboard.php
```
#25: 'NOTIFY_ADMIN_DASHBOARD_WIDGETS', null, $widgets

```

#### admin/categories.php
```
#40: 'NOTIFY_BEGIN_ADMIN_CATEGORIES', $action
#193: 'NOTIFY_ADMIN_CATEGORIES_UPDATE_OR_INSERT_FINISH', ['action' => $action, 'categories_id' => (int)$categories_id]
#352: 'NOTIFY_ADMIN_CATEGORIES_EXTRA_INPUTS', $cInfo, $extra_category_inputs

```

#### admin/customers.php
```
#176: 'NOTIFY_ADMIN_CUSTOMERS_UPDATE_VALIDATE', [], $error
#253: 'NOTIFY_ADMIN_CUSTOMERS_CUSTOMER_UPDATE', $customers_id, $sql_data_array
#341:  'NOTIFY_ADMIN_CUSTOMERS_B4_ADDRESS_UPDATE', ['customers_id' => $customers_id, 'address_book_id' => $default_address_id], $sql_data_array 
#365:  'NOTIFY_ADMIN_CUSTOMER_UPDATE', $customers_id, $default_address_id, $sql_data_array 
#460: 'NOTIFIER_ADMIN_ZEN_CUSTOMERS_DELETE_CONFIRM', ['customers_id' => $customers_id]
#710: 'NOTIFY_ADMIN_CUSTOMERS_CUSTOMER_EDIT', $cInfo, $additional_fields
#1358: 'NOTIFY_ADMIN_CUSTOMERS_LISTING_HEADER', [], $additional_headings
#1570:  'NOTIFY_ADMIN_CUSTOMERS_LISTING_NEW_FIELDS', [], $new_fields, $disp_order 
#1691:  'NOTIFY_ADMIN_CUSTOMERS_LISTING_ELEMENT', array_merge($result, $customer), $additional_columns, $customer 
#1982:  'NOTIFY_ADMIN_CUSTOMERS_PLACE_ORDER_BUTTON', $cInfo, $contents, $place_order_override 
#2025: 'NOTIFY_ADMIN_CUSTOMERS_MENU_BUTTONS', $cInfo, $contents
#2131: 'NOTIFY_ADMIN_CUSTOMERS_MENU_BUTTONS_END', $cInfo ?? new stdClass, $contents

```

#### admin/orders.php
```
#77: 'NOTIFY_ADMIN_ORDER_PREDISPLAY_HOOK', $oID, $action
#240: 'NOTIFY_ADMIN_ORDERS_UPDATE_ORDER_START', $oID
#389: 'NOTIFY_ADMIN_ORDERS_DEFAULT_ACTION', $oID, $order, $action
#429: 'NOTIFY_ADMIN_ORDERS_HEADING_TITLE', ['action' => $action, 'order_exists' => $order_exists, 'oID' => $oID], $heading_title, $extra_top_content
#504: 'NOTIFY_ADMIN_ORDERS_EDIT_BEGIN', $oID, $order
#552: 'NOTIFY_ADMIN_ORDERS_UPPER_BUTTONS', $oID, $left_side_buttons, $right_side_buttons
#596: 'NOTIFY_ADMIN_ORDERS_ADDRESS_FOOTERS', 'customer', $address_footer_suffix, $order->customer
#630: 'ADMIN_ORDERS_IP_LINKS', $lookup_ip, $whois_url, $whois_provider_url, $lookup_ip2, $whois_url2
#674: 'NOTIFY_ADMIN_ORDERS_ADDRESS_FOOTERS', 'delivery', $address_footer_suffix, $order->delivery
#707: 'NOTIFY_ADMIN_ORDERS_ADDRESS_FOOTERS', 'billing', $address_footer_suffix, $order->billing
#824: <?php 'NOTIFY_ADMIN_ORDERS_PAYMENTDATA_COLUMN2', $oID, $order ?>
#1003: 'NOTIFY_ADMIN_ORDERS_CONTENT_UNDER_PRODUCTS', ['oID' => $oID], $extra_content
#1035: 'NOTIFY_ADMIN_ORDERS_STATUS_HISTORY_EXTRA_COLUMN_HEADING', [], $extra_headings
#1086: 'NOTIFY_ADMIN_ORDERS_STATUS_HISTORY_EXTRA_COLUMN_DATA', $item, $extra_data
#1123: 'NOTIFY_ADMIN_ORDERS_AFTER_STATUS_LISTING', $oID, $additional_content
#1147: 'NOTIFY_ADMIN_ORDERS_ADDL_HISTORY_INPUTS', []
#1169: 'NOTIFY_ADMIN_ORDERS_EXTRA_STATUS_INPUTS', $order, $extra_status_inputs
#1217: 'NOTIFY_ADMIN_ORDERS_EDIT_BUTTONS', $oID, $order, $extra_buttons
#1247: 'NOTIFY_ADMIN_ORDERS_MENU_LEGEND', [], $extra_legends
#1283: 'NOTIFY_ADMIN_ORDERS_LIST_EXTRA_COLUMN_HEADING', [], $extra_headings
#1348: 'NOTIFY_ADMIN_ORDERS_SEARCH_PARMS', $keywords, $search, $search_distinct, $new_fields, $new_table, $order_by
#1414: 'NOTIFY_ADMIN_ORDERS_SHOW_ORDER_DIFFERENCE', [], $orders->fields, $show_difference, $extra_action_icons
#1500: 'NOTIFY_ADMIN_ORDERS_LIST_EXTRA_COLUMN_DATA', ($oInfo ?? []), $orders->fields, $extra_data
#1579: 'NOTIFY_ADMIN_ORDERS_MENU_BUTTONS', $oInfo, $contents
#1657: 'NOTIFY_ADMIN_ORDERS_MENU_BUTTONS_END', ($oInfo ?? []), $contents

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
