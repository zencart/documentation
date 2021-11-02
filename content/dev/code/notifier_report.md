---
title: Notifier Report 
description: Output of the Zen Cart Notifier Report plugin 
category: code
type: codepage
weight: 10
---

Run on Zen Cart 1.5.7c.

<!-- RELEASETIME - update -->

<!-- 
To generate this file, run notifier_report.php?markdown on 
an installation of the latest version of Zen Cart.  Get the notifier report
from https://github.com/lat9/notifier_report 
--> 


#### build_additional.php
```
#41:  'NOTIFY_MODULES_ADDITIONAL_IMAGES_FILE_MATCH', array( 'file' => $file, 'file_extension' => $file_extension, 'products_image' => $products_image, 'products_image_base' => $products_image_base ), $current_image_match 

```

#### ipn_main_handler.php
```
#304: 'NOTIFY_CHECKOUT_PROCESS_BEFORE_ORDER_TOTALS_PROCESS'
#306: 'NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_TOTALS_PROCESS'
#318: 'NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_CREATE'
#325: 'NOTIFY_CHECKOUT_PROCESS_AFTER_PAYMENT_MODULES_AFTER_ORDER_CREATE'
#352: 'NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_CREATE_ADD_PRODUCTS'
#355: 'NOTIFY_CHECKOUT_PROCESS_AFTER_SEND_ORDER_EMAIL'
#389: 'NOTIFY_CHECKOUT_PROCESS_HANDLE_AFFILIATES', 'paypalipn'
#470: 'NOTIFY_PAYPALIPN_STATUS_HISTORY_UPDATE', array($ordersID, $new_status, $txn_type)

```

#### includes/classes/shopping_cart.php
```
#77: 'NOTIFIER_CART_INSTANTIATE_START'
#79: 'NOTIFIER_CART_INSTANTIATE_END'
#99: 'NOTIFIER_CART_RESTORE_CONTENTS_START'
#182: 'NOTIFIER_CART_RESTORE_CONTENTS_END'
#198: 'NOTIFIER_CART_RESET_START', array(), $reset_database
#220: 'NOTIFIER_CART_RESET_END'
#255: 'NOTIFIER_CART_ADD_CART_START', array(), $products_id, $qty, $attributes, $notify
#343: 'NOTIFIER_CART_ADD_CART_END', array(), $products_id, $qty, $attributes, $notify
#367: 'NOTIFIER_CART_UPDATE_QUANTITY_START', array(), $products_id, $quantity, $attributes
#443: 'NOTIFIER_CART_UPDATE_QUANTITY_END'
#457: 'NOTIFIER_CART_CLEANUP_START'
#475: 'NOTIFIER_CART_CLEANUP_END'
#490: 'NOTIFIER_CART_COUNT_CONTENTS_START'
#497: 'NOTIFIER_CART_COUNT_CONTENTS_END'
#510: 'NOTIFIER_CART_GET_QUANTITY_START', array(), $products_id
#512: 'NOTIFIER_CART_GET_QUANTITY_END_QTY', array(), $products_id
#515: 'NOTIFIER_CART_GET_QUANTITY_END_FALSE', $products_id
#526: 'NOTIFIER_CART_IN_CART_START', array(), $products_id
#528: 'NOTIFIER_CART_IN_CART_END_TRUE', array(), $products_id
#531: 'NOTIFIER_CART_IN_CART_END_FALSE', $products_id
#543: 'NOTIFIER_CART_REMOVE_START', array(), $products_id
#560: 'NOTIFIER_CART_REMOVE_END'
#568: 'NOTIFIER_CART_REMOVE_ALL_START'
#570: 'NOTIFIER_CART_REMOVE_ALL_END'
#624: 'NOTIFY_CART_CALCULATE_PRODUCT_PRICE', $products_id, $product->fields
#702: 'NOTIFY_CART_CALCULATE_ATTRIBUTE_PRICE', $products_id, $attribute_price->fields
#867: 'NOTIFY_CART_CALCULATE_ATTRIBUTE_WEIGHT', array('products_id' => $products_id, 'options_id' => $option), $attribute_weight->fields
#934: 'NOTIFY_CART_ATTRIBUTES_PRICE_START', $products_id
#953: 'NOTIFY_CART_ATTRIBUTES_PRICE_NEXT', $products_id, $attribute_price->fields
#1044: 'NOTIFY_CART_ATTRIBUTES_PRICE_ONETIME_CHARGES_START', $products_id
#1061: 'NOTIFY_CART_ATTRIBUTES_PRICE_ONETIME_CHARGES_NEXT', $products_id, $attribute_price->fields
#1122: 'NOTIFY_CART_ATTRIBUTES_WEIGHT_START', $products_id
#1137: 'NOTIFY_CART_ATTRIBUTES_WEIGHT_NEXT', $products_id, $attribute_weight_info->fields
#1170: 'NOTIFIER_CART_GET_PRODUCTS_START', array(), $check_for_valid_cart
#1184: 'NOTIFY_CART_GET_PRODUCTS_NEXT', $products_id, $products->fields
#1351: 'NOTIFIER_CART_GET_PRODUCTS_END', array(), $products_array
#1360: 'NOTIFIER_CART_SHOW_TOTAL_START'
#1362: 'NOTIFIER_CART_SHOW_TOTAL_END'
#1372: 'NOTIFIER_CART_SHOW_TOTAL_BEFORE_DISCOUNT_START'
#1374: 'NOTIFIER_CART_SHOW_TOTAL_BEFORE_DISCOUNT_END'
#1977: 'NOTIFIER_CART_OPTIONAL_ATTRIBUTE_ERROR_MESSAGE_HOOK', $_POST, $the_list
#2216: 'NOTIFY_CART_USER_ACTION', array(), $goto, $parameters

```

#### includes/classes/order.php
```
#30: 'NOTIFY_ORDER_INSTANTIATE', array(), $order_id
#47: 'NOTIFY_ORDER_BEFORE_QUERY', array(), $order_id
#78: 'NOTIFY_ORDER_COUPON_LINK', $coupon_link->fields, $zc_coupon_link
#232: 'NOTIFY_ORDER_QUERY_ADD_PRODUCT', $this->products[$index], $index
#238: 'NOTIFY_ORDER_AFTER_QUERY', IS_ADMIN_FLAG, $this->orderId
#244: 'ORDER_QUERY_ADMIN_COMPLETE', array('orders_id' => $this->orderId)
#252: 'NOTIFY_ORDER_CART_BEGINS'
#424: 'NOTIFY_ORDER_CART_AFTER_ADDRESSES_SET', '', $taxCountryId, $taxZoneId
#455: 'NOTIFY_ORDER_CART_ADD_PRODUCT_LIST', array('index'=>$index, 'products'=>$products[$i])
#492: 'NOTIFY_ORDER_CART_ADD_ATTRIBUTE_LIST', array('index'=>$index, 'subindex'=>$subindex, 'products'=>$products[$i], 'attributes'=>$attributes)
#523: 'NOTIFY_ORDER_CART_FINISHED'
#577: 'NOTIFY_ORDER_CART_EXTERNAL_TAX_RATE_LOOKUP', STORE_PRODUCT_TAX_BASIS, $products, $loop, $index, $taxCountryId, $taxZoneId, $taxRates
#604: 'NOTIFY_ORDER_CART_EXTERNAL_TAX_HANDLING', array(), $index, $taxCountryId, $taxZoneId
#614: 'NOTIFY_ORDER_CART_SUBTOTAL_CALCULATE', array('shown_price' => $shown_price)
#647: 'NOTIFY_ORDER_CART_EXTERNAL_TAX_DURING_ORDER_CREATE', array(), $zf_ot_modules
#658: 'NOTIFY_ORDER_CART_ORDERSTATUS'
#724: 'NOTIFY_ORDER_DURING_CREATE_ADDED_ORDER_HEADER', array_merge(array('orders_id' => $this->orderId, 'shipping_weight' => $_SESSION['cart']->weight), $sql_data_array), $this->orderId
#737: 'NOTIFY_ORDER_DURING_CREATE_ADDED_ORDERTOTAL_LINE_ITEM', $sql_data_array, $ot_insert_id
#764: 'NOTIFY_ORDER_DURING_CREATE_ADDED_ORDER_COMMENT', $sql_data_array, $osh_insert_id
#792: 'NOTIFY_ORDER_PROCESSING_STOCK_DECREMENT_INIT', array('i'=>$i), $this->products[$i], $i
#816: 'NOTIFY_ORDER_PROCESSING_STOCK_DECREMENT_BEGIN', $i, $stock_values
#843: 'NOTIFY_ORDER_PROCESSING_BESTSELLERS_UPDATE', array(), $this->products[$i], $i
#848: 'NOTIFY_ORDER_PROCESSING_STOCK_DECREMENT_END', $i
#877: 'NOTIFY_ORDER_DURING_CREATE_ADDED_PRODUCT_LINE_ITEM', array_merge(array('orders_products_id' => $order_products_id, 'i' => $i), $sql_data_array), $order_products_id
#879: 'NOTIFY_ORDER_PROCESSING_CREDIT_ACCOUNT_UPDATE_BEGIN'
#882: 'NOTIFY_ORDER_PROCESSING_ATTRIBUTES_BEGIN'
#960: 'NOTIFY_ORDER_DURING_CREATE_ADDED_ATTRIBUTE_LINE_ITEM', array_merge(array('orders_products_attributes_id' => $opa_insert_id), $sql_data_array), $opa_insert_id
#974: 'NOTIFY_ORDER_DURING_CREATE_ADDED_ATTRIBUTE_DOWNLOAD_LINE_ITEM', $sql_data_array, $opd_insert_id
#980: 'NOTIFY_ORDER_PROCESSING_ATTRIBUTES_EXIST', $attributes_exist
#982: 'NOTIFY_ORDER_DURING_CREATE_ADD_PRODUCTS', $i, $custom_insertable_text
#1010: 'NOTIFY_ORDER_PROCESSING_ONE_TIME_CHARGES_BEGIN', $i
#1034: 'NOTIFY_ORDER_AFTER_ORDER_CREATE_ADD_PRODUCTS'
#1047: 'NOTIFY_ORDER_SEND_EMAIL_INITIALIZE', array(), $zf_insert_id, $order_totals, $zf_mode
#1051: 'NOTIFY_ORDER_SEND_LOW_STOCK_EMAILS'
#1096: 'NOTIFY_ORDER_EMAIL_BEFORE_PRODUCTS', array(), $email_order, $html_msg
#1160: 'NOTIFY_ORDER_SET_ORDER_MESSAGE'
#1182: 'NOTIFY_ORDER_INVOICE_CONTENT_READY_TO_SEND', array('zf_insert_id' => $zf_insert_id, 'text_email' => $email_order, 'html_email' => $html_msg), $email_order, $html_msg, $send_customer_email
#1203: 'NOTIFY_ORDER_INVOICE_CONTENT_FOR_ADDITIONAL_EMAILS', $zf_insert_id, $email_order, $html_msg
#1210: 'NOTIFY_ORDER_AFTER_SEND_ORDER_EMAIL', $zf_insert_id, $email_order, $extra_info, $html_msg

```

#### includes/classes/shipping.php
```
#26: 'NOTIFY_SHIPPING_CLASS_GET_INSTALLED_MODULES', $module
#63: 'NOTIFY_SHIPPING_MODULE_ENABLE', $include_modules[$i]['class'], $include_modules[$i]['class']
#82: 'NOTIFY_SHIPPING_CHECK_ENABLED_FOR_ZONE', array(), $class, $enabled
#87: 'NOTIFY_SHIPPING_CHECK_ENABLED', array(), $class, $enabled
#95: 'NOTIFY_SHIPPING_MODULE_PRE_CALCULATE_BOXES_AND_TARE', array(), $total_weight, $shipping_weight, $shipping_quoted, $shipping_num_boxes
#143: 'NOTIFY_SHIPPING_MODULE_CALCULATE_BOXES_AND_TARE', array(), $total_weight, $shipping_weight, $shipping_quoted, $shipping_num_boxes
#179: 'NOTIFY_SHIPPING_MODULE_GET_ALL_QUOTES', $quotes_array, $quotes_array
#221: 'NOTIFY_SHIPPING_MODULE_CALCULATE_CHEAPEST', $cheapest, $cheapest, $rates

```

#### includes/classes/TableViewControllers/BaseController.php
```
#194: 'ADMIN_VIEW_CONTROLLER_GET_ACTION', $action
#255: 'TABLE_CONTROLLER_SET_TABLE_DESC_DEFAULTS'

```

#### includes/classes/payment.php
```
#27: 'NOTIFY_PAYMENT_CLASS_GET_INSTALLED_MODULES', $module
#78: 'NOTIFY_PAYMENT_MODULE_ENABLE'

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

#### includes/init_includes/init_languages.php
```
#18: 'NOTIFY_LANGUAGE_CHANGE_REQUESTED_BY_VISITOR', $_GET['language'], $lng

```

#### includes/init_includes/init_canonical.php
```
#41: 'NOTIFY_INIT_CANONICAL_PARAM_WHITELIST', $current_page, $excludeParams, $keepableParams, $includeCPath
#112: 'NOTIFY_INIT_CANONICAL_DEFAULT', $current_page, $excludeParams, $canonicalLink
#114: 'NOTIFY_INIT_CANONICAL_FINAL', $current_page, $excludeParams, $canonicalLink

```

#### includes/init_includes/init_customer_auth.php
```
#57: 'NOTIFY_LOGIN_BANNED'

```

#### includes/functions/html_output.php
```
#17: 'NOTIFY_SEFU_INTERCEPT', array(), $link, $page, $parameters, $connection, $add_session_id, $static, $use_dir_ws_catalog
#201: 'NOTIFY_HANDLE_IMAGE', array($newimg)
#204: 'NOTIFY_OPTIMIZE_IMAGE', $template_dir, $src, $alt, $width, $height, $parameters
#282: 'PAGE_OUTPUT_IMAGE_SUBMIT'
#306: 'PAGE_OUTPUT_IMAGE_BUTTON'
#358:  'NOTIFY_ZEN_CSS_BUTTON_SUBMIT', array( 'button_name' => $button_name, 'text' => $text, 'sec_class' => $sec_class, 'parameters' => $parameters, ), $css_button 
#380:  'NOTIFY_ZEN_CSS_BUTTON_BUTTON', array( 'button_name' => $button_name, 'text' => $text, 'sec_class' => $sec_class, 'parameters' => $parameters, ), $css_button 
#435:  'NOTIFY_ZEN_DRAW_INPUT_FIELD_OVERRIDE', array( 'name' => $name, 'value' => $value, 'parameters' => $parameters, 'type' => $type, 'reinsert_value' => $reinsert_value, 'required' => $required, ), $field 
#465:  'NOTIFY_ZEN_DRAW_INPUT_FIELD', array( 'name' => $name, 'value' => $value, 'parameters' => $parameters, 'type' => $type, 'reinsert_value' => $reinsert_value, 'required' => $required, ), $field 
#500:  'NOTIFY_ZEN_DRAW_SELECTION_FIELD_OVERRIDE', array( 'name' => $name, 'value' => $value, 'parameters' => $parameters, 'type' => $type, 'checked' => $checked ), $selection 
#535:  'NOTIFY_ZEN_DRAW_SELECTION_FIELD', array( 'name' => $name, 'value' => $value, 'parameters' => $parameters, 'type' => $type, 'checked' => $checked ), $selection 
#571:  'NOTIFY_ZEN_DRAW_TEXTAREA_FIELD_OVERRIDE', array( 'name' => $name, 'width' => $width, 'height' => $height, 'text' => $text, 'parameters' => $parameters, 'reinsert_value' => $reinsert_value, ), $field 
#604:  'NOTIFY_ZEN_DRAW_TEXTAREA_FIELD', array( 'name' => $name, 'width' => $width, 'height' => $height, 'text' => $text, 'parameters' => $parameters, 'reinsert_value' => $reinsert_value, ), $field 
#679:  'NOTIFY_ZEN_DRAW_PULL_DOWN_MENU_OVERRIDE', array( 'name' => $name, 'values' => $values, 'default' => $default, 'parameters' => $parameters, 'required' => $required, ), $field 
#728:  'NOTIFY_ZEN_DRAW_PULL_DOWN_MENU', array( 'name' => $name, 'values' => $values, 'default' => $default, 'parameters' => $parameters, 'required' => $required, ), $field 

```

#### includes/functions/functions_products.php
```
#76: 'NOTIFY_PRODUCT_INFO_PRODUCT_STATUS_CHECK', $product_info->fields, $product_status, $should_throw_404, $response_code, $use_custom_response_code

```

#### includes/functions/functions_prices.php
```
#130: 'ZEN_GET_PRODUCTS_BASE_PRICE', $products_id, $products_base_price, $base_price_is_handled
#240:  'NOTIFY_ZEN_GET_PRODUCTS_DISPLAY_PRICE_SALE', array( 'products_id' => $products_id, 'display_sale_price' => $display_sale_price, 'display_special_price' => $display_special_price, 'display_normal_price' => $display_normal_price, 'products_tax_class_id' => $product_check->fields['products_tax_class_id'] ), $pricing_handled, $show_sale_discount 
#280:  'NOTIFY_ZEN_GET_PRODUCTS_DISPLAY_PRICE_SPECIAL', array( 'products_id' => $products_id, 'display_sale_price' => $display_sale_price, 'display_special_price' => $display_special_price, 'display_normal_price' => $display_normal_price, 'products_tax_class_id' => $product_check->fields['products_tax_class_id'], 'product_is_free' => $product_check->fields['product_is_free'] ), $pricing_handled, $show_normal_price, $show_special_price, $show_sale_price 
#318:  'NOTIFY_ZEN_GET_PRODUCTS_DISPLAY_PRICE_NORMAL', array( 'products_id' => $products_id, 'display_sale_price' => $display_sale_price, 'display_special_price' => $display_special_price, 'display_normal_price' => $display_normal_price, 'products_tax_class_id' => $product_check->fields['products_tax_class_id'], 'product_is_free' => $product_check->fields['product_is_free'] ), $pricing_handled, $show_normal_price, $show_special_price, $show_sale_price 
#361:  'NOTIFY_ZEN_GET_PRODUCTS_DISPLAY_PRICE_FREE_OR_CALL', array( 'product_is_free' => $product_check->fields['product_is_free'], 'product_is_call' => $product_check->fields['product_is_call'], ), $tags_handled, $free_tag, $call_tag 

```

#### includes/functions/functions_osh_update.php
```
#70: 'ZEN_UPDATE_ORDERS_HISTORY_PRE_EMAIL', array('message' => $message), $osh_additional_comments
#88: 'ZEN_UPDATE_ORDERS_HISTORY_STATUS_VALUES', array('orders_id' => $orders_id, 'new' => $orders_new_status, 'old' => $orders_current_status)
#126: 'ZEN_UPDATE_ORDERS_HISTORY_SET_ORDER_UPDATE_MESSAGE', $orders_id, $email_order_message
#192: 'ZEN_UPDATE_ORDERS_HISTORY_BEFORE_INSERT', array(), $osh_sql

```

#### includes/functions/functions_customers.php
```
#97:  'NOTIFY_END_ZEN_ADDRESS_FORMAT', array( 'format' => $fmt, 'address' => $incoming, 'firstname' => $address['$firstname'], 'lastname' => $address['$lastname'], 'street' => $address['$street'], 'suburb' => $address['$suburb'], 'city' => $address['$city'], 'state' => $address['$state'], 'country' => $address['$country'], 'postcode' => $address['$postcode'], 'company' => $address['$company'], 'streets' => $address['$streets'], 'statecomma' => $address['$statecomma'], 'zip' => $address['$zip'], 'cr' => $address['$cr'], 'hr' => $address['$hr'], ), $address_out 
#139: 'NOTIFY_ZEN_ADDRESS_LABEL', array(), $customers_id, $address_id, $address->fields
#264: 'NOTIFY_ZEN_IN_GUEST_CHECKOUT', '', $in_guest_checkout
#274: 'NOTIFY_ZEN_IS_LOGGED_IN', '', $is_logged_in

```

#### includes/functions/functions_lookups.php
```
#164:  'ZEN_GET_PRODUCTS_STOCK', $products_id, $products_quantity, $quantity_handled 
#199:  'ZEN_CHECK_STOCK_MESSAGE', array( $products_id, $products_quantity ), $out_of_stock_message 
#301: 'NOTIFY_FUNCTIONS_LOOKUPS_REQUIRES_ATTRIBUTES_SELECTION', '', $query, $noSingles, $noDoubles
#357: 'FUNCTIONS_LOOKUPS_OPTION_NAME_NO_VALUES_OPT_TYPE', $opt_type, $test_var
#378: 'NOTIFY_ZEN_HAS_PRODUCT_ATTRIBUTES_VALUES', $products_id, $value_to_return

```

#### includes/functions/functions_general.php
```
#627: 'NOTIFY_ZEN_INVALID_IP_DETECTED', $original_ip

```

#### includes/functions/functions_taxes.php
```
#19:  'NOTIFY_ZEN_GET_TAX_RATE_OVERRIDE', array( 'class_id' => $class_id, 'country_id' => $country_id, 'zone_id' => $zone_id ), $tax_rate 
#83:  'NOTIFY_ZEN_GET_TAX_DESCRIPTION_OVERRIDE', array( 'class_id' => $class_id, 'country_id' => $country_id, 'zone_id' => $zone_id ), $tax_description 
#142:  'NOTIFY_ZEN_GET_MULTIPLE_TAX_RATES_OVERRIDE', array( 'class_id' => $class_id, 'country_id' => $country_id, 'zone_id' => $zone_id, 'tax_description' => $tax_description ), $rates_array 
#284:  'ZEN_GET_TAX_LOCATIONS', array( 'country' => $store_country, 'zone' => $store_zone ), $tax_address 
#347:  'NOTIFY_ZEN_GET_ALL_TAX_DESCRIPTIONS_OVERRIDE', array( 'country_id' => $country_id, 'zone_id' => $zone_id ), $tax_descriptions 

```

#### includes/functions/functions_email.php
```
#92: 'NOTIFY_EMAIL_ADDRESS_TEST', array(), $to_name, $to_email_address, $email_subject
#95: 'NOTIFY_EMAIL_ADDRESS_VALIDATION_FAILURE', sprintf(EMAIL_SEND_FAILED . ' (failed validation)', $to_name, $to_email_address, $email_subject)
#171: 'NOTIFY_EMAIL_DETERMINING_EMAIL_FORMAT', $to_email_address, $customers_email_format, $module
#191: 'NOTIFY_EMAIL_AFTER_EMAIL_FORMAT_DETERMINED'
#282: 'NOTIFY_EMAIL_BEFORE_PROCESS_ATTACHMENTS', array('attachments'=>$attachments_list, 'module'=>$module), $mail, $attachments_list
#312: 'NOTIFY_EMAIL_AFTER_PROCESS_ATTACHMENTS', sizeof($attachments_list)
#354: 'NOTIFY_EMAIL_READY_TO_SEND', array($mail), $mail
#371: 'NOTIFY_EMAIL_AFTER_SEND'
#376: 'NOTIFY_EMAIL_AFTER_SEND_WITH_ALL_PARAMS', array($to_name, $to_email_address, $from_email_name, $from_email_address, $email_subject, $email_html, $text, $module, $ErrorInfo)
#383: 'NOTIFY_EMAIL_AFTER_SEND_ALL_SPECIFIED_ADDRESSES'
#410: 'NOTIFY_EMAIL_BEGIN_ARCHIVE_WRITE', array($to_name, $to_email_address, $from_email_name, $from_email_address, $email_subject, $email_html, $email_text, $module, $error_msgs)
#740: 'NOTIFY_EMAIL_VALIDATION_TEST', array($email, $valid_address)

```

#### includes/templates/responsive_classic/common/tpl_columnar_display.php
```
#12: 'NOTIFY_TPL_COLUMNAR_DISPLAY_START', $current_page_base, $list_box_contents, $title
#45: 'NOTIFY_TPL_COLUMNAR_DISPLAY_END', $current_page_base, $list_box_contents, $title

```

#### includes/templates/responsive_classic/common/main_template_vars.php
```
#20: 'NOTIFY_MAIN_TEMPLATE_VARS_START', $template_dir
#52: 'NOTIFY_MAIN_TEMPLATE_VARS_END', $template_dir, $body_code

```

#### includes/templates/responsive_classic/common/html_header.php
```
#16: 'NOTIFY_HTML_HEAD_START', $current_page_base, $template_dir
#212: 'NOTIFY_HTML_HEAD_END', $current_page_base

```

#### includes/templates/responsive_classic/common/tpl_main_page.php
```
#266: 'NOTIFY_FOOTER_END', $current_page

```

#### includes/templates/responsive_classic/common/tpl_tabular_display.php
```
#13: 'NOTIFY_TPL_TABULAR_DISPLAY_START', $current_page_base, $list_box_contents
#50: 'NOTIFY_TPL_TABULAR_DISPLAY_END', $current_page_base, $list_box_contents

```

#### includes/templates/template_default/common/tpl_columnar_display.php
```
#12: 'NOTIFY_TPL_COLUMNAR_DISPLAY_START', $current_page_base, $list_box_contents, $title
#45: 'NOTIFY_TPL_COLUMNAR_DISPLAY_END', $current_page_base, $list_box_contents, $title

```

#### includes/templates/template_default/common/main_template_vars.php
```
#20: 'NOTIFY_MAIN_TEMPLATE_VARS_START', $template_dir
#38: 'NOTIFY_MAIN_TEMPLATE_VARS_END', $template_dir, $body_code

```

#### includes/templates/template_default/common/html_header.php
```
#16: 'NOTIFY_HTML_HEAD_START', $current_page_base, $template_dir
#166: 'NOTIFY_HTML_HEAD_END', $current_page_base

```

#### includes/templates/template_default/common/tpl_main_page.php
```
#195: 'NOTIFY_FOOTER_END', $current_page

```

#### includes/templates/template_default/common/tpl_tabular_display.php
```
#13: 'NOTIFY_TPL_TABULAR_DISPLAY_START', $current_page_base, $list_box_contents
#48: 'NOTIFY_TPL_TABULAR_DISPLAY_END', $current_page_base, $list_box_contents

```

#### includes/modules/featured_products.php
```
#68: 'NOTIFY_MODULES_FEATURED_PRODUCTS_B4_LIST_BOX', array(), $featured_products->fields, $products_price

```

#### includes/modules/main_product_image.php
```
#17: 'NOTIFY_MODULES_MAIN_PRODUCT_IMAGE_START'
#39:  'NOTIFY_MODULES_MAIN_PRODUCT_IMAGE_FILENAME', $products_image, $main_image_handled, $products_image_extension, $products_image_base, $products_image_medium, $products_image_large 
#76: 'NOTIFY_MODULES_MAIN_PRODUCT_IMAGE_END'

```

#### includes/modules/specials_index.php
```
#72: 'NOTIFY_MODULES_SPECIALS_INDEX_B4_LIST_BOX', array(), $specials_index->fields, $products_price

```

#### includes/modules/responsive_classic/ezpages_bar_header.php
```
#12: 'NOTIFY_START_EZPAGES_HEADERBAR'
#71: 'NOTIFY_END_EZPAGES_HEADERBAR'

```

#### includes/modules/responsive_classic/product_listing.php
```
#33: 'NOTIFY_MODULE_PRODUCT_LISTING_RESULTCOUNT', $listing_split->number_of_rows
#198: 'NOTIFY_MODULES_PRODUCT_LISTING_PRODUCTS_BUTTON', array(), $listing->fields, $lc_button
#286: 'NOTIFY_PRODUCT_LISTING_END', $current_page_base, $list_box_contents, $listing_split, $show_top_submit_button, $show_bottom_submit_button, $show_submit, $how_many

```

#### includes/modules/checkout_new_address.php
```
#10: 'NOTIFY_MODULE_START_CHECKOUT_NEW_ADDRESS'
#134: 'NOTIFY_MODULE_CHECKOUT_NEW_ADDRESS_VALIDATION', array(), $error
#160: 'NOTIFY_MODULE_CHECKOUT_ADDED_ADDRESS_BOOK_RECORD', array_merge(array('address_id' => $address_book_id ), $sql_data_array)
#254: 'NOTIFY_MODULE_END_CHECKOUT_NEW_ADDRESS'

```

#### includes/modules/meta_tags.php
```
#15: 'NOTIFY_MODULE_START_META_TAGS', $current_page_base, $metatag_page_name, $meta_tags_over_ride
#34: 'NOTIFY_MODULE_META_TAGS_BUILDKEYWORDS', CUSTOM_KEYWORDS, $keywords_string_metatags
#333: 'NOTIFY_MODULE_META_TAGS_UNSPECIFIEDPAGE', $current_page_base, $metatag_page_name, $meta_tags_over_ride, $metatags_title, $metatags_description, $metatags_keywords
#341: 'NOTIFY_MODULE_META_TAGS_OVERRIDE', $metatag_page_name, $meta_tags_over_ride, $metatags_title, $metatags_description, $metatags_keywords
#351: 'NOTIFY_MODULE_END_META_TAGS'

```

#### includes/modules/attributes.php
```
#118: 'NOTIFY_ATTRIBUTES_MODULE_START_OPTION', $products_options_names->fields
#151: 'NOTIFY_ATTRIBUTES_MODULE_START_OPTIONS_LOOP', $i++, $products_options->fields, $products_options_names->fields, $data_properties, $field_disabled, $attributeDetailsArrayForJson
#207: 'NOTIFY_ATTRIBUTES_MODULE_SALEMAKER_DISPLAY_PRICE_PERCENTAGE', $products_options->fields, $product_info->fields, $products_options_display_price, $data_properties
#227: 'NOTIFY_ATTRIBUTES_MODULE_ORIGINAL_PRICE', $products_options->fields, $products_options_array, $products_options_display_price, $data_properties
#300: 'NOTIFY_ATTRIBUTES_MODULE_RADIO_SELECTED', $products_options->fields, $data_properties
#389: 'NOTIFY_ATTRIBUTES_MODULE_CHECKBOX_SELECTED', $products_options->fields, $data_properties
#522: 'NOTIFY_ATTRIBUTES_MODULE_FORMAT_VALUE', array_merge($products_options->fields, $products_options_names->fields), $data_properties, $field_disabled, $attributeDetailsArrayForJson
#562: 'NOTIFY_ATTRIBUTES_MODULE_BEFORE_ASSEMBLE_OUTPUTS', $products_options->fields, $data_properties, $inputFieldId, $field_disabled
#638: 'NOTIFY_ATTRIBUTES_MODULE_DEFAULT_SWITCH', $products_options_names->fields, $options_name, $options_menu, $options_comment, $options_comment_position, $options_html_id, $data_properties, $options_inputfield_id
#645: 'NOTIFY_ATTRIBUTES_MODULE_OPTION_BUILT', $products_options_names->fields, $options_name, $options_menu, $options_comment, $options_comment_position, $options_html_id, $options_attributes_image, $data_properties, $options_inputfield_id
#650: 'NOTIFY_ATTRIBUTES_MODULE_END', $prod_id, $options_name, $options_menu, $options_comment, $options_comment_position, $options_html_id, $options_attributes_image, $options_inputfield_id, $attributeDetailsArrayForJson

```

#### includes/modules/create_account.php
```
#10: 'NOTIFY_MODULE_START_CREATE_ACCOUNT'
#41: 'NOTIFY_CREATE_ACCOUNT_CAPTCHA_CHECK'
#148: 'NOTIFY_CREATE_ACCOUNT_LOOKUP_BY_EMAIL', $email_address, $check_email_query, $send_welcome_email
#156: 'NOTIFY_NICK_CHECK_FOR_EXISTING_EMAIL', $email_address, $nick_error, $nick
#166: 'NOTIFY_NICK_CHECK_FOR_MIN_LENGTH', $nick, $nick_error, $nick_length_min
#168: 'NOTIFY_NICK_CHECK_FOR_DUPLICATE', $nick, $nick_error
#258: 'NOTIFY_CREATE_ACCOUNT_VALIDATION_CHECK', array(), $error, $send_welcome_email
#270: 'NOTIFY_FAILURE_DURING_CREATE_ACCOUNT'
#272: 'NOTIFY_SPAM_DETECTED_DURING_CREATE_ACCOUNT'
#297: 'NOTIFY_MODULE_CREATE_ACCOUNT_ADDED_CUSTOMER_RECORD', array_merge(array('customer_id' => $_SESSION['customer_id']), $sql_data_array)
#327: 'NOTIFY_MODULE_CREATE_ACCOUNT_ADDED_ADDRESS_BOOK_RECORD', array_merge(array('address_id' => $address_id), $sql_data_array)
#344: 'NOTIFY_NICK_CREATE_NEW', $nick, $password, $nick_email, $extra_welcome_text
#361: 'NOTIFY_LOGIN_SUCCESS_VIA_CREATE_ACCOUNT', $email_address, $extra_welcome_text, $send_welcome_email
#467: 'NOTIFY_NICK_SET_TEMPLATE_FLAG', 0, $display_nick_field
#471: 'NOTIFY_MODULE_END_CREATE_ACCOUNT'

```

#### includes/modules/payment/authorizenet.php
```
#346: 'NOTIFY_PAYMENT_AUTHNETSIM_PRESUBMIT_HOOK'
#419: 'NOTIFY_PAYMENT_AUTHNETSIM_POSTSUBMIT_HOOK', $this->authorize
#458: 'NOTIFY_PAYMENT_AUTHNETSIM_POSTPROCESS_HOOK'

```

#### includes/modules/payment/paypaldp.php
```
#1082: 'NOTIFY_PAYMENT_PAYPALDP_INSTALLED'
#1098: 'NOTIFY_PAYMENT_PAYPALDP_UNINSTALLED'
#1483: 'NOTIFY_PAYMENT_PAYPALDP_SUBTOTALS_REVIEW', $order, $order_totals

```

#### includes/modules/payment/paypalwpp.php
```
#426: 'NOTIFY_PAYPALWPP_BEFORE_DOEXPRESSCHECKOUT'
#477: 'NOTIFY_PAYPALWPP_BEFORE_PROCESS_FINISHED', $response
#545: 'NOTIFY_PAYPALWPP_AFTER_PROCESS_FINISHED', $paypal_order
#700: 'NOTIFY_PAYMENT_PAYPALWPP_INSTALLED'
#743: 'NOTIFY_PAYMENT_PAYPALWPP_UNINSTALLED'
#1245: 'NOTIFY_PAYMENT_PAYPALEC_SUBTOTALS_TAX', $order, $order_totals
#1337: 'NOTIFY_PAYPALWPP_GETLINEITEMDETAILS', $numberOfLineItemsProcessed, $optionsLI
#1662: 'NOTIFY_PAYMENT_PAYPALEC_BEFORE_SETEC', array(), $options, $order, $order_totals
#1670: 'NOTIFY_PAYMENT_PAYPALEC_TOKEN', $response, $options
#1785: 'NOTIFY_PAYPALEC_PARSE_GETEC_RESULT', array(), $response
#1822: 'NOTIFY_PAYPAL_EXPRESS_CHECKOUT_PAYERID_DETERMINED', $response['PAYERID']
#1953: 'NOTIFY_PAYPAL_CUSTOMER_ATTEMPT_TO_USE_INVALID_COUNTRY_CODE'
#2041: 'NOTIFY_PAYPALEXPRESS_BYPASS_ADDRESS_CREATION', $paypal_ec_payer_info, $bypass_address_creation
#2151: 'NOTIFY_PAYPALEXPRESS_CREATE_ACCOUNT_ADDED_CUSTOMER_RECORD', $customer_id, $sql_data_array
#2182: 'NOTIFY_PAYPALEXPRESS_CREATE_ACCOUNT_ADDED_ADDRESS_BOOK_RECORD', array(), $address_id, $sql_data_array
#2235: 'NOTIFY_LOGIN_SUCCESS_VIA_CREATE_ACCOUNT', 'paypal express checkout'
#2276: 'NOTIFY_PAYPALEC_END_ECSTEP2', $order
#2348: 'NOTIFY_PAYPALWPP_DISABLE_GET_OVERRIDE_ADDRESS', $address_id, $disable_address_override
#2607: 'NOTIFY_HEADER_ADDRESS_BOOK_ADD_ENTRY_INVALID_ATTEMPT', $customer_id, $country_id, $address_format_id, $address_question_arr
#2670: 'NOTIFY_HEADER_ADDRESS_BOOK_ADD_ENTRY_DONE', 'paypal express checkout', $new_address_book_id, $sql_data_array, $make_default
#2925: 'NOTIFY_PAYPALWPP_ERROR_HANDLER', $response, $operation, $basicError, $ignoreList, $errorInfo

```

#### includes/modules/payment/firstdata_hco.php
```
#294: 'MODULE_PAYMENT_FIRSTDATA_PAYMENTPAGES_PRESUBMIT_HOOK'
#347: 'MODULE_PAYMENT_FIRSTDATA_PAYMENTPAGES_POSTSUBMIT_HOOK', $this->authorize
#381: 'MODULE_PAYMENT_FIRSTDATA_PAYMENTPAGES_POSTPROCESS_HOOK'

```

#### includes/modules/payment/paypal/paypal_curl.php
```
#108: 'NOTIFY_PAYPAL_CURL_CONSTRUCT', $params
#155: 'NOTIFY_PAYPAL_SETEXPRESSCHECKOUT'
#171: 'NOTIFY_PAYPAL_GETEXPRESSCHECKOUTDETAILS'
#195: 'NOTIFY_PAYPAL_DOEXPRESSCHECKOUTPAYMENT'
#238: 'NOTIFY_PAYPAL_DODIRECTPAYMENT'
#560: 'NOTIFY_PAYPAL_CURL_BUILDNAMEVALUELIST', $string
#661: 'PAYPAL_CURL_LOG', $token, $tokenHash

```

#### includes/modules/payment/authorizenet_aim.php
```
#399: 'NOTIFY_PAYMENT_AUTHNET_EMULATOR_CHECK', $this->code, $submit_data
#414: 'NOTIFY_PAYMENT_AUTHNET_PRESUBMIT_HOOK', $this->code, $submit_data
#420: 'NOTIFY_PAYMENT_AUTHNET_POSTSUBMIT_HOOK', $this->code, $response
#604: 'NOTIFY_PAYMENT_AUTHNET_MODE_SELECTION', $this->mode, $submit_data
#684: 'NOTIFY_PAYMENT_AUTHNET_ENCAPSULATION_CHECK'

```

#### includes/modules/payment/paypal.php
```
#355: 'NOTIFY_PAYMENT_PAYPAL_RETURN_TO_STORE', $_GET
#380: 'NOTIFY_PAYMENT_PAYPAL_CANCELLED_DURING_CHECKOUT', $_GET
#531: 'NOTIFY_PAYMENT_PAYPAL_INSTALLED'
#540: 'NOTIFY_PAYMENT_PAYPAL_UNINSTALLED'

```

#### includes/modules/downloads.php
```
#108: 'NOTIFY_MODULE_DOWNLOAD_TEMPLATE_DETAILS', $data, $data

```

#### includes/modules/product_listing_alpha_sorter.php
```
#28: 'NOTIFY_PRODUCT_LISTING_ALPHA_SORTER_SELECTLIST', isset($prefix) ? $prefix : '', $letters_list

```

#### includes/modules/additional_images.php
```
#14: 'NOTIFY_MODULES_ADDITIONAL_PRODUCT_IMAGES_START'
#54:  'NOTIFY_MODULES_ADDITIONAL_IMAGES_FILE_MATCH', array( 'file' => $file, 'file_extension' => $file_extension, 'products_image' => $products_image, 'products_image_base' => $products_image_base ), $current_image_match 
#84: 'NOTIFY_MODULES_ADDITIONAL_PRODUCT_IMAGES_LIST', NULL, $images_array
#111: 'NOTIFY_MODULES_ADDITIONAL_IMAGES_GET_LARGE', $products_name, $products_image_large
#126: 'NOTIFY_MODULES_ADDITIONAL_IMAGES_THUMB_SLASHES', array(), $thumb_slashes
#145:  'NOTIFY_MODULES_ADDITIONAL_IMAGES_SCRIPT_LINK', array( 'flag_display_large' => $flag_display_large, 'products_name' => $products_name, 'products_image_large' => $products_image_large, 'thumb_slashes' => $thumb_slashes, 'large_link' => $large_link, 'index' => $i ), $script_link, $link_parameters 
#182: 'NOTIFY_MODULES_ADDITIONAL_PRODUCT_IMAGES_END'

```

#### includes/modules/checkout_address_book.php
```
#26: 'NOTIFY_MODULE_END_CHECKOUT_ADDRESS_BOOK', $addresses_query, $addresses

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
#81: 'NOTIFY_CHECKOUT_PROCESS_BEFORE_ORDER_TOTALS_PROCESS'
#83: 'NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_TOTALS_PROCESS'
#91: 'NOTIFY_CHECKOUT_PROCESS_AFTER_PAYMENT_MODULES_BEFOREPROCESS'
#94: 'NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_CREATE', $insert_id
#96: 'NOTIFY_CHECKOUT_PROCESS_AFTER_PAYMENT_MODULES_AFTER_ORDER_CREATE', $insert_id
#100: 'NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_CREATE_ADD_PRODUCTS', $insert_id, $order
#103: 'NOTIFY_CHECKOUT_PROCESS_AFTER_SEND_ORDER_EMAIL', $insert_id, $order
#143: 'NOTIFY_CHECKOUT_PROCESS_HANDLE_AFFILIATES'

```

#### includes/modules/ezpages_bar_footer.php
```
#12: 'NOTIFY_START_EZPAGES_FOOTERBAR'
#70: 'NOTIFY_END_EZPAGES_FOOTERBAR'

```

#### includes/modules/product_listing.php
```
#14: 'NOTIFY_MODULE_PRODUCT_LISTING_RESULTCOUNT', $listing_split->number_of_rows
#148: 'NOTIFY_MODULES_PRODUCT_LISTING_PRODUCTS_BUTTON', array(), $listing->fields, $lc_button
#203: 'NOTIFY_PRODUCT_LISTING_END', $current_page_base, $list_box_contents, $listing_split, $show_top_submit_button, $show_bottom_submit_button, $show_submit, $how_many

```

#### includes/modules/order_total/ot_shipping.php
```
#72:  'NOTIFY_OT_SHIPPING_TAX_CALCS', array(), $external_shipping_tax_handler, $shipping_tax, $shipping_tax_description 

```

#### includes/modules/order_total/ot_coupon.php
```
#189:  'NOTIFY_OT_COUPON_COUPON_REMOVED' 
#234:  'NOTIFY_OT_COUPON_COUPON_INFO', array( 'coupon_result' => $coupon_result->fields, 'code' => $dc_check ) 
#351: 'NOTIFY_OT_COUPON_USES_PER_USER_CHECK', $coupon_result->fields, $coupon_uses_per_user_exceeded
#626:  'NOTIFY_OT_COUPON_CALCS_FINISHED', array( 'coupon' => $coupon, 'order_totals' => $orderTotalDetails, 'od_amount' => $od_amount, ) 
#650:  'NOTIFY_OT_COUPON_PRODUCT_VALIDITY', array( 'is_product_valid' => $is_product_valid, 'i' => $i ) 

```

#### includes/modules/new_products.php
```
#70: 'NOTIFY_MODULES_NEW_PRODUCTS_B4_LIST_BOX', array(), $new_products->fields, $products_price

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
#12: 'NOTIFY_HEADER_START_CREATE_ACCOUNT_SUCCESS'
#65: 'NOTIFY_HEADER_END_CREATE_ACCOUNT_SUCCESS'

```

#### includes/modules/pages/account_history_info/header_php.php
```
#10: 'NOTIFY_HEADER_START_ACCOUNT_HISTORY_INFO'
#61: 'NOTIFY_HEADER_END_ACCOUNT_HISTORY_INFO'

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
#18: 'NOTIFY_PRODUCT_TYPE_VARS_START_PRODUCT_FREE_SHIPPING_INFO'
#36: 'NOTIFY_PRODUCT_TYPE_VARS_END_PRODUCT_FREE_SHIPPING_INFO'

```

#### includes/modules/pages/account_history/header_php.php
```
#10: 'NOTIFY_HEADER_START_ACCOUNT_HISTORY'
#69: 'NOTIFY_HEADER_END_ACCOUNT_HISTORY'

```

#### includes/modules/pages/checkout_payment/header_php.php
```
#12: 'NOTIFY_HEADER_START_CHECKOUT_PAYMENT'
#123: 'NOTIFY_HEADER_END_CHECKOUT_PAYMENT'

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
#18: 'NOTIFY_PRODUCT_TYPE_VARS_START_DOCUMENT_GENERAL_INFO'
#36: 'NOTIFY_PRODUCT_TYPE_VARS_END_DOCUMENT_GENERAL_INFO'

```

#### includes/modules/pages/checkout_confirmation/header_php.php
```
#11: 'NOTIFY_HEADER_START_CHECKOUT_CONFIRMATION'
#169: 'NOTIFY_HEADER_END_CHECKOUT_CONFIRMATION'

```

#### includes/modules/pages/product_reviews/header_php.php
```
#12: 'NOTIFY_HEADER_START_PRODUCT_REVIEWS'
#87: 'NOTIFY_HEADER_END_PRODUCT_REVIEWS'

```

#### includes/modules/pages/contact_us/header_php.php
```
#11: 'NOTIFY_HEADER_START_CONTACT_US'
#28: 'NOTIFY_CONTACT_US_CAPTCHA_CHECK', $_POST
#35: 'NOTIFY_SPAM_DETECTED_USING_CONTACT_US', $_POST
#55: 'NOTIFY_CONTACT_US_ACTION', (isset($_SESSION['customer_id']) ? $_SESSION['customer_id'] : 0), $customer_email, $customer_name, $email_address, $name, $enquiry, $telephone
#146: 'NOTIFY_HEADER_END_CONTACT_US'

```

#### includes/modules/pages/featured_products/header_php.php
```
#11: 'NOTIFY_HEADER_START_FEATURED_PRODUCTS'
#36: 'NOTIFY_FEATURED_PRODUCTS_SQL_STRING', array(), $featured_products_query_raw, $count_key
#83: 'NOTIFY_HEADER_END_FEATURED_PRODUCTS', $how_many

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
#10: 'NOTIFY_HEADER_START_SPECIALS'

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
#12: 'NOTIFY_HEADER_START_PAGE_NOT_FOUND'
#28: 'NOTIFY_HEADER_END_PAGE_NOT_FOUND'

```

#### includes/modules/pages/password_forgotten/header_php.php
```
#11: 'NOTIFY_HEADER_START_PASSWORD_FORGOTTEN'
#42: 'NOTIFY_PASSWORD_FORGOTTEN_VALIDATED', $email_address
#62: 'NOTIFY_PASSWORD_FORGOTTEN_CHANGED', $email_address, $check_customer->fields['customers_id'], $new_password
#65: 'NOTIFY_PASSWORD_FORGOTTEN_NOT_FOUND', $email_address
#77: 'NOTIFY_HEADER_END_PASSWORD_FORGOTTEN'

```

#### includes/modules/pages/unsubscribe/header_php.php
```
#12: 'NOTIFY_HEADER_START_UNSUBSCRIBE'
#57: 'NOTIFY_HEADER_END_UNSUBSCRIBE'

```

#### includes/modules/pages/account_newsletters/header_php.php
```
#11: 'NOTIFY_HEADER_START_ACCOUNT_NEWSLETTERS'
#46: 'NOTIFY_HEADER_ACCOUNT_NEWSLETTER_UPDATED', $newsletter_general
#57: 'NOTIFY_HEADER_END_ACCOUNT_NEWSLETTERS'

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
#18: 'NOTIFY_PRODUCT_TYPE_VARS_START_DOCUMENT_PRODUCT_INFO'
#36: 'NOTIFY_PRODUCT_TYPE_VARS_END_DOCUMENT_PRODUCT_INFO'

```

#### includes/modules/pages/gv_redeem/header_php.php
```
#9: 'NOTIFY_HEADER_START_GV_REDEEM'

```

#### includes/modules/pages/popup_image/header_php.php
```
#15: 'NOTIFY_HEADER_START_POPUP_IMAGES_ADDITIONAL'
#64: 'NOTIFY_HEADER_END_POPUP_IMAGES'

```

#### includes/modules/pages/time_out/header_php.php
```
#12: 'NOTIFY_HEADER_START_LOGIN'
#13: 'NOTIFY_HEADER_START_LOGIN_TIMEOUT'
#79: 'NOTIFY_LOGIN_SUCCESS'
#105: 'NOTIFY_LOGIN_FAILURE'
#110: 'NOTIFY_HEADER_END_LOGIN_TIMEOUT'
#111: 'NOTIFY_HEADER_END_LOGIN'

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
#12: 'NOTIFY_HEADER_START_CHECKOUT_PAYMENT_ADDRESS'
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
#141: 'NOTIFY_HEADER_END_PRODUCT_REVIEWS_WRITE'

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
#16: 'NOTIFY_HEADER_START_PRODUCT_REVIEWS_INFO'
#117: 'NOTIFY_HEADER_END_PRODUCT_REVIEWS_INFO'

```

#### includes/modules/pages/logoff/header_php.php
```
#12: 'NOTIFY_HEADER_START_LOGOFF'
#33: 'NOTIFY_HEADER_END_LOGOFF'

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

#### includes/modules/pages/advanced_search_result/header_php.php
```
#11: 'NOTIFY_HEADER_START_ADVANCED_SEARCH_RESULTS'
#33: 'NOTIFY_ADVANCED_SEARCH_RESULTS_ADDL_CLAUSE', array(), $search_additional_clause
#215: 'NOTIFY_SEARCH_COLUMNLIST_STRING'
#229: 'NOTIFY_SEARCH_SELECT_STRING'
#262: 'NOTIFY_SEARCH_FROM_STRING'
#415: 'NOTIFY_SEARCH_WHERE_STRING'
#477: 'NOTIFY_SEARCH_ORDERBY_STRING', $listing_sql
#494: 'NOTIFY_HEADER_END_ADVANCED_SEARCH_RESULTS', $keywords

```

#### includes/modules/pages/index/main_template_vars.php
```
#12: 'NOTIFY_HEADER_START_INDEX_MAIN_TEMPLATE_VARS'
#55: 'NOTIFY_HEADER_INDEX_MAIN_TEMPLATE_VARS_RELEASE_PRODUCT_TYPE_VARS'
#229: 'NOTIFY_HEADER_INDEX_MAIN_TEMPLATE_VARS_PAGE_BODY', NULL, $tpl_page_body, $current_categories_name
#234: 'NOTIFY_HEADER_END_INDEX_MAIN_TEMPLATE_VARS', NULL, $current_categories_description

```

#### includes/modules/pages/index/header_php.php
```
#11: 'NOTIFY_HEADER_START_INDEX'
#63:  'NOTIFY_INDEX_CATEGORY_STATUS_CHECK', array('cPath' => $cPath, 'current_category_id' => $current_category_id), $category_redirect_handled, $current_category_not_found, $current_category_is_disabled, $current_category_has_products, $current_category_has_subcats, $category_depth 
#146: 'NOTIFY_HEADER_END_INDEX'

```

#### includes/modules/pages/product_info/main_template_vars.php
```
#14: 'NOTIFY_MAIN_TEMPLATE_VARS_START_PRODUCT_INFO'
#34: 'NOTIFY_PRODUCT_VIEWS_HIT_INCREMENTOR', (int)$_GET['products_id']
#109: 'NOTIFY_MAIN_TEMPLATE_VARS_PRODUCT_TYPE_VARS_PRODUCT_INFO'
#149: 'NOTIFY_MAIN_TEMPLATE_VARS_EXTRA_PRODUCT_INFO'
#157: 'NOTIFY_MAIN_TEMPLATE_VARS_END_PRODUCT_INFO'

```

#### includes/modules/pages/product_info/header_php.php
```
#11: 'NOTIFY_HEADER_START_PRODUCT_INFO'
#25: 'NOTIFY_HEADER_END_PRODUCT_INFO'

```

#### includes/modules/pages/product_info/main_template_vars_product_type.php
```
#18: 'NOTIFY_PRODUCT_TYPE_VARS_START_PRODUCT_INFO'
#36: 'NOTIFY_PRODUCT_TYPE_VARS_END_PRODUCT_INFO'

```

#### includes/modules/pages/gv_faq/header_php.php
```
#11: 'NOTIFY_HEADER_START_GV_FAQ'
#35: 'NOTIFY_HEADER_END_GV_FAQ'

```

#### includes/modules/pages/account_notifications/header_php.php
```
#10: 'NOTIFY_HEADER_START_ACCOUNT_NOTIFICATION'
#136: 'NOTIFY_HEADER_END_ACCOUNT_NOTIFICATION'

```

#### includes/modules/pages/address_book/header_php.php
```
#11: 'NOTIFY_HEADER_START_ADDRESS_BOOK'
#48: 'NOTIFY_HEADER_END_ADDRESS_BOOK'

```

#### includes/modules/pages/create_account/header_php.php
```
#12: 'NOTIFY_HEADER_START_CREATE_ACCOUNT'
#21: 'NOTIFY_HEADER_END_CREATE_ACCOUNT'

```

#### includes/modules/pages/account/header_php.php
```
#10: 'NOTIFY_HEADER_START_ACCOUNT'
#72: 'NOTIFY_HEADER_END_ACCOUNT'

```

#### includes/modules/pages/account_password/header_php.php
```
#11: 'NOTIFY_HEADER_START_ACCOUNT_PASSWORD'
#56: 'NOTIFY_HEADER_ACCOUNT_PASSWORD_CHANGED', $_SESSION['customer_id'], $password_new, $check_customer->fields['customers_nick']
#73: 'NOTIFY_HEADER_END_ACCOUNT_PASSWORD'

```

#### includes/modules/pages/checkout_shipping_address/header_php.php
```
#12: 'NOTIFY_HEADER_START_CHECKOUT_SHIPPING_ADDRESS'
#57: 'NOTIFY_HEADER_END_CHECKOUT_SHIPPING_ADDRESS'

```

#### includes/modules/pages/shopping_cart/header_php.php
```
#11: 'NOTIFY_HEADER_START_SHOPPING_CART'
#160: 'NOTIFY_HEADER_END_SHOPPING_CART'

```

#### includes/modules/pages/account_edit/header_php.php
```
#10: 'NOTIFY_HEADER_START_ACCOUNT_EDIT'
#93: 'NOTIFY_NICK_CHECK_FOR_EXISTING_EMAIL', $email_address, $nick_error, $nick
#102: 'NOTIFY_HEADER_ACCOUNT_EDIT_VERIFY_COMPLETE'
#106: 'NOTIFY_NICK_UPDATE_EMAIL_ADDRESS', $nick, $email_address
#151: 'NOTIFY_HEADER_ACCOUNT_EDIT_UPDATES_COMPLETE'
#208: 'NOTIFY_HEADER_END_ACCOUNT_EDIT'

```

#### includes/modules/pages/site_map/header_php.php
```
#12: 'NOTIFY_HEADER_START_SITE_MAP'
#26: 'NOTIFY_HEADER_END_SITE_MAP'

```

#### includes/modules/pages/login/header_php.php
```
#10: 'NOTIFY_HEADER_START_LOGIN'
#75: 'NOTIFY_LOGIN_BANNED'
#91: 'NOTIFY_PROCESS_3RD_PARTY_LOGINS', $email_address, $password, $loginAuthorized
#137: 'NOTIFY_LOGIN_SUCCESS'
#182: 'NOTIFY_LOGIN_FAILURE'
#194: 'NOTIFY_HEADER_END_LOGIN'

```

#### includes/modules/pages/checkout_process/header_php.php
```
#11: 'NOTIFY_HEADER_START_CHECKOUT_PROCESS'
#18: 'NOTIFY_CHECKOUT_PROCESS_BEFORE_CART_RESET', $insert_id
#30: 'NOTIFY_HEADER_END_CHECKOUT_PROCESS'

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
#353: 'NOTIFY_HEADER_END_ADDRESS_BOOK_PROCESS'

```

#### admin/attributes_controller.php
```
#347: 'NOTIFY_ATTRIBUTE_CONTROLLER_ADD_PRODUCT_ATTRIBUTES', $products_attributes_id
#492: 'NOTIFY_ATTRIBUTE_CONTROLLER_UPDATE_PRODUCT_ATTRIBUTE', $attribute_id
#505: 'NOTIFY_ATTRIBUTE_CONTROLLER_DELETE_ATTRIBUTE', ['attribute_id' => $attribute_id], $attribute_id
#522: 'NOTIFY_ATTRIBUTE_CONTROLLER_DELETE_ALL', ['pID' => $_POST['products_filter']]
#536: 'NOTIFY_ATTRIBUTE_CONTROLLER_DELETE_OPTION_NAME_VALUES', ['pID' => $_POST['products_filter'], 'options_id' => $_POST['products_options_id_all']]
#749: 'NOTIFY_ATTRIBUTE_CONTROLLER_ADDITIONAL_ACTIONS_DROPDOWN_UPPER', $zc_products, $action, $products_filter, $current_category_id
#755: 'NOTIFY_ATTRIBUTE_CONTROLLER_ADDITIONAL_ACTIONS_DROPDOWN_SUBMENU', $zc_products, $action, $products_filter, $current_category_id

```

#### admin/product.php
```
#14: 'NOTIFY_BEGIN_ADMIN_PRODUCTS', $action

```

#### admin/languages.php
```
#178: 'NOTIFY_ADMIN_LANGUAGE_INSERT', (int)$insert_id
#255: 'NOTIFY_ADMIN_LANGUAGE_DELETE', (int)$lID

```

#### admin/category_product_listing.php
```
#352: 'NOTIFY_ADMIN_PROD_LISTING_DEFAULT_ACTION'
#624: 'NOTIFY_ADMIN_PROD_LISTING_HEADERS_B4_QTY', '', $extra_headings
#659: 'NOTIFY_ADMIN_PROD_LISTING_HEADERS_AFTER_QTY', '', $extra_headings
#794: 'NOTIFY_ADMIN_PROD_LISTING_PRODUCTS_QUERY', '', $extra_select, $extra_from, $extra_joins, $extra_ands, $order_by
#897: 'NOTIFY_ADMIN_PROD_LISTING_DATA_B4_QTY', '', $extra_data
#928: 'NOTIFY_ADMIN_PROD_LISTING_DATA_AFTER_QTY', '', $extra_data
#941: 'NOTIFY_ADMIN_PROD_LISTING_ADD_ICON', $product, $additional_icons

```

#### admin/admin_activity.php
```
#293: 'NOTIFY_ADMIN_ACTIVITY_LOG_RESET'

```

#### admin/includes/classes/class.admin.zcObserverLogEventListener.php
```
#57: $this->notifier->notify('NOTIFY_ADMIN_FIRE_LOG_WRITERS', $log_data
#192: $this->notifier->notify('NOTIFY_ADMIN_FIRE_LOG_WRITER_RESET'
#208: 'NOTIFY_ADMIN_ACTIVITY_LOG_EVENT', $message, $severity

```

#### admin/includes/init_includes/init_languages.php
```
#21: 'NOTIFY_LANGUAGE_CHANGE_REQUESTED_BY_ADMIN_VISITOR', $_GET['language'], $lng

```

#### admin/includes/init_includes/init_admin_history.php
```
#12: 'NOTIFY_ADMIN_ACTIVITY_LOG_EVENT', 'POST'

```

#### admin/includes/attributes_preview.php
```
#95: 'NOTIFY_ATTRIBUTES_MODULE_START_OPTION', $products_options_names->fields
#105: 'NOTIFY_ATTRIBUTES_MODULE_START_OPTIONS_LOOP', array(), $products_options->fields
#594: 'NOTIFY_ATTRIBUTES_MODULE_DEFAULT_SWITCH', $products_options_names->fields, $options_name, $options_menu, $options_comment, $options_comment_position, $options_html_id
#601: 'NOTIFY_ATTRIBUTES_MODULE_OPTION_BUILT', $products_options_names->fields, $options_name, $options_menu, $options_comment, $options_comment_position, $options_html_id, $options_attributes_image

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

#### admin/includes/functions/functions_prices.php
```
#119: 'ZEN_GET_PRODUCTS_BASE_PRICE', $products_id, $products_base_price, $base_price_is_handled

```

#### admin/includes/functions/localization.php
```
#41: 'ADMIN_CURRENCY_EXCHANGE_RATE_MULTIPLIER', $currency->fields['code'], $multiplier, $rate
#52: 'ADMIN_CURRENCY_EXCHANGE_RATE_SINGLE', $currency->fields['code'], $rate
#74: 'ADMIN_CURRENCY_EXCHANGE_RATES_UPDATED', $msg

```

#### admin/includes/functions/general.php
```
#1103: 'NOTIFIER_ADMIN_ZEN_REMOVE_CATEGORY', array(), $category_id
#1264: 'NOTIFIER_ADMIN_ZEN_REMOVE_PRODUCT', array(), $product_id, $ptc
#1354: 'NOTIFIER_ADMIN_ZEN_PRODUCTS_ATTRIBUTES_DOWNLOAD_DELETE', array(), $product_id
#1366: 'NOTIFIER_ADMIN_ZEN_REMOVE_ORDER', array(), $order_id, $restock
#1582:  'NOTIFY_ZEN_GET_TAX_RATE_OVERRIDE', array( 'class_id' => $class_id, 'country_id' => $country_id, 'zone_id' => $zone_id ), $tax_rate 
#2023: 'FUNCTIONS_LOOKUPS_OPTION_NAME_NO_VALUES_OPT_TYPE', $opt_type, $test_var
#2059: 'ZEN_COPY_PRODUCTS_ATTRIBUTES_START', array('from' => (int)$products_id_from, 'to' => (int)$products_id_to)
#2072: 'ZEN_COPY_PRODUCTS_ATTRIBUTES_DELETE', (int)$products_id_to
#2154: 'ZEN_COPY_PRODUCTS_ATTRIBUTES_ADD', array('pID' => (int)$products_id_to, 'fields' => $products_copy_from->fields)
#2194: 'ZEN_COPY_PRODUCTS_ATTRIBUTES_UPDATE', array('pID' => (int)$products_id_to, 'fields' => $products_copy_from->fields)
#2203: 'ZEN_COPY_PRODUCTS_ATTRIBUTES_COMPLETE', array('from' => (int)$products_id_from, 'to' => (int)$products_id_to)
#2301: 'NOTIFIER_ADMIN_ZEN_DELETE_PRODUCTS_ATTRIBUTES', array(), $delete_product_id
#3293: 'NOTIFY_TEST_DOWNLOADABLE_FILE_EXISTS', $check_filename, $handler
#3668: 'NOTIFY_ZEN_ADMIN_INVALID_IP_DETECTED', $original_ip

```

#### admin/includes/modules/new_product_preview.php
```
#24: 'NOTIFY_ADMIN_PRODUCT_IMAGE_UPLOADED', $products_image, $products_image_name

```

#### admin/includes/modules/update_product.php
```
#126: 'NOTIFY_MODULES_UPDATE_PRODUCT_END', array('action' => $action, 'products_id' => $products_id)

```

#### admin/includes/modules/product_free_shipping/collect_info.php
```
#209: 'NOTIFY_ADMIN_PRODUCT_COLLECT_INFO_EXTRA_INPUTS', $pInfo, $extra_product_inputs

```

#### admin/includes/modules/document_general/collect_info.php
```
#217: 'NOTIFY_ADMIN_PRODUCT_COLLECT_INFO_EXTRA_INPUTS', $pInfo, $extra_product_inputs

```

#### admin/includes/modules/document_product/collect_info.php
```
#206: 'NOTIFY_ADMIN_PRODUCT_COLLECT_INFO_EXTRA_INPUTS', $pInfo, $extra_product_inputs

```

#### admin/includes/modules/product/collect_info.php
```
#209: 'NOTIFY_ADMIN_PRODUCT_COLLECT_INFO_EXTRA_INPUTS', $pInfo, $extra_product_inputs

```

#### admin/includes/modules/copy_product_confirm.php
```
#76: 'NOTIFY_MODULES_COPY_PRODUCT_CONFIRM_DUPLICATE_FIELDS', $product, $separately_updated_fields, $casted_fields
#198: 'NOTIFY_MODULES_COPY_TO_CONFIRM_DUPLICATE', compact('products_id', 'dup_products_id')

```

#### admin/includes/modules/product_music/update_product.php
```
#142: 'NOTIFY_PRODUCT_MUSIC_UPDATE_PRODUCT_END', array('action' => $action, 'products_id' => $products_id)

```

#### admin/includes/modules/product_music/collect_info.php
```
#242: 'NOTIFY_ADMIN_PRODUCT_COLLECT_INFO_EXTRA_INPUTS', $pInfo, $extra_product_inputs

```

#### admin/includes/modules/product_music/copy_product_confirm.php
```
#76: 'NOTIFY_MODULES_COPY_PRODUCT_CONFIRM_DUPLICATE_FIELDS', $product, $separately_updated_fields, $casted_fields
#151: 'NOTIFY_PRODUCT_MUSIC_COPY_TO_CONFIRM_DUPLICATE', compact('products_id', 'dup_products_id')
#229: 'NOTIFY_PRODUCT_MUSIC_COPY_TO_CONFIRM_DUPLICATE', compact('products_id', 'dup_products_id')

```

#### admin/includes/modules/product_music/copy_product.php
```
#49: 'NOTIFY_ADMIN_PRODUCT_COPY_TO_ATTRIBUTES', $pInfo, $contents

```

#### admin/includes/modules/copy_product.php
```
#48: 'NOTIFY_ADMIN_PRODUCT_COPY_TO_ATTRIBUTES', $pInfo, $contents

```

#### admin/options_values_manager.php
```
#163: 'OPTIONS_VALUES_MANAGER_DELETE_VALUE', array('value_id' => $value_id)
#475: 'OPTIONS_VALUES_MANAGER_DELETE_VALUES_OF_OPTIONNAME', array('current_products_id' => $current_products_id, 'remove_ids' => $remove_downloads_ids, 'options_id' => $options_id_from, 'options_values_id' => $options_values_values_id_from)

```

#### admin/whos_online.php
```
#243: 'ADMIN_WHOSONLINE_IP_LINKS', $item, $additional_ipaddress_links, $whois_url

```

#### admin/ezpages.php
```
#136: 'NOTIFY_ADMIN_EZPAGES_UPDATE_BASE', $action, $page_error, $sql_data_array
#168: 'NOTIFY_ADMIN_EZPAGES_UPDATE_LANG_INSERT', array('pages_id' => (int)$pages_id, 'languages_id' => $language_id), $sql_data_array
#184: 'NOTIFY_ADMIN_EZPAGES_UPDATE_LANG_UPDATE', array('pages_id' => (int)$pages_id, 'languages_id' => $language_id), $sql_data_array
#299: 'NOTIFY_ADMIN_EZPAGES_NEW', '', $parameters
#372: 'NOTIFY_ADMIN_EZPAGES_FORM_FIELDS', $ezInfo, $extra_page_inputs
#620: 'NOTIFY_ADMIN_EZPAGES_EXTRA_ACTION_ICONS', $page, $extra_action_icons

```

#### admin/coupon_admin.php
```
#95: 'ADMIN_COUPON_CODE_EMAILED_TO_CUSTOMER', $coupon_result->fields['coupon_code'], $mail->fields['customers_email_address']

```

#### admin/categories.php
```
#41: 'NOTIFY_BEGIN_ADMIN_CATEGORIES', $action
#352: 'NOTIFY_ADMIN_CATEGORIES_EXTRA_INPUTS', $cInfo, $extra_category_inputs

```

#### admin/customers.php
```
#35: 'NOTIFY_ADMIN_CUSTOMERS_LIST_ADDRESSES', $addresses_query
#244: 'NOTIFY_ADMIN_CUSTOMERS_UPDATE_VALIDATE', array(), $error
#302: 'NOTIFY_ADMIN_CUSTOMERS_B4_ADDRESS_UPDATE', array('customers_id' => $customers_id, 'address_book_id' => $default_address_id), $sql_data_array
#306: 'ADMIN_CUSTOMER_UPDATE', (int)$customers_id, $default_address_id, $sql_data_array
#366: 'NOTIFIER_ADMIN_ZEN_CUSTOMERS_DELETE_CONFIRM', array('customers_id' => $customers_id)
#731: 'NOTIFY_ADMIN_CUSTOMERS_CUSTOMER_EDIT', $cInfo, $additional_fields
#1127: 'NOTIFY_ADMIN_CUSTOMERS_LISTING_HEADER', array(), $additional_headings
#1201: 'NOTIFY_ADMIN_CUSTOMERS_LISTING_NEW_FIELDS', array(), $new_fields, $disp_order
#1311: 'NOTIFY_ADMIN_CUSTOMERS_LISTING_ELEMENT', $customer, $additional_columns
#1402: 'NOTIFY_ADMIN_CUSTOMERS_PLACE_ORDER_BUTTON', $cInfo, $contents, $place_order_override
#1427: 'NOTIFY_ADMIN_CUSTOMERS_MENU_BUTTONS', $cInfo, $contents
#1460: 'NOTIFY_ADMIN_CUSTOMERS_MENU_BUTTONS_END', (isset($cInfo) ? $cInfo : new stdClass), $contents

```

#### admin/orders.php
```
#98: 'NOTIFY_ADMIN_ORDER_PREDISPLAY_HOOK', $oID, $action
#272: 'NOTIFY_ADMIN_ORDERS_UPDATE_ORDER_START', $oID
#437: 'NOTIFY_ADMIN_ORDERS_DEFAULT_ACTION', $oID, $order
#571: 'NOTIFY_ADMIN_ORDERS_EDIT_BEGIN', $oID, $order
#607: 'NOTIFY_ADMIN_ORDERS_UPPER_BUTTONS', $oID, $left_side_buttons, $right_side_buttons
#649: 'NOTIFY_ADMIN_ORDERS_ADDRESS_FOOTERS', 'customer', $address_footer_suffix, $order->customer
#672: 'ADMIN_ORDERS_IP_LINKS', $lookup_ip, $whois_url
#697: 'NOTIFY_ADMIN_ORDERS_ADDRESS_FOOTERS', 'delivery', $address_footer_suffix, $order->delivery
#716: 'NOTIFY_ADMIN_ORDERS_ADDRESS_FOOTERS', 'billing', $address_footer_suffix, $order->billing
#768: <?php 'NOTIFY_ADMIN_ORDERS_PAYMENTDATA_COLUMN2', $oID, $order ?>
#920: 'NOTIFY_ADMIN_ORDERS_STATUS_HISTORY_EXTRA_COLUMN_HEADING', array(), $extra_headings
#974: 'NOTIFY_ADMIN_ORDERS_STATUS_HISTORY_EXTRA_COLUMN_DATA', $orders_history->fields, $extra_data
#1011: 'NOTIFY_ADMIN_ORDERS_AFTER_STATUS_LISTING', $oID, $additional_content
#1043: 'NOTIFY_ADMIN_ORDERS_ADDL_HISTORY_INPUTS', array()
#1065: 'NOTIFY_ADMIN_ORDERS_EXTRA_STATUS_INPUTS', $order, $extra_status_inputs
#1113: 'NOTIFY_ADMIN_ORDERS_EDIT_BUTTONS', $oID, $order, $extra_buttons
#1143: 'NOTIFY_ADMIN_ORDERS_MENU_LEGEND', array(), $extra_legends
#1204: 'NOTIFY_ADMIN_ORDERS_LIST_EXTRA_COLUMN_HEADING', array(), $extra_headings
#1243: 'NOTIFY_ADMIN_ORDERS_SEARCH_PARMS', $keywords, $search, $search_distinct, $new_fields, $new_table, $order_by
#1306: 'NOTIFY_ADMIN_ORDERS_SHOW_ORDER_DIFFERENCE', array(), $orders->fields, $show_difference, $extra_action_icons
#1371: 'NOTIFY_ADMIN_ORDERS_LIST_EXTRA_COLUMN_DATA', (isset($oInfo) ? $oInfo : array()), $orders->fields, $extra_data
#1447: 'NOTIFY_ADMIN_ORDERS_MENU_BUTTONS', $oInfo, $contents
#1514: 'NOTIFY_ADMIN_ORDERS_MENU_BUTTONS_END', (isset($oInfo) ? $oInfo : array()), $contents

```

#### admin/options_name_manager.php
```
#178: 'OPTIONS_NAME_MANAGER_DELETE_OPTION', ['option_id' => $option_id, 'options_values_id' => (int)$remove_option_value['products_options_values_id']]
#297: 'OPTIONS_NAME_MANAGER_UPDATE_OPTIONS_VALUES_DELETE', [ 'products_id' => $all_update_product['products_id'], 'options_id' => $all_options_value['products_options_id'], 'options_values_id' => $all_options_value['products_options_values_id'] ] 

```

#### image_purge_utility.php
```
#267:  'NOTIFY_MODULES_ADDITIONAL_IMAGES_FILE_MATCH', array( 'file' => $file, 'file_extension' => $file_extension, 'products_image' => $products_image, 'products_image_base' => $products_image_base ), $current_image_match 

```
