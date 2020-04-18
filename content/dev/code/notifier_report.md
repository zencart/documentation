---
title: Notifier Report 
description: Zen Cart Notifier Report
category: code
type: codepage
weight: 10
---

<!-- RELEASETIME - update -->

<!-- 
To generate this file, run notifier_report.php?markdown on 
an installation of the latest version of Zen Cart.  Get the notifier report
from https://github.com/lat9/notifier_report 
--> 

#### ipn_main_handler.php
```
#305: 'NOTIFY_CHECKOUT_PROCESS_BEFORE_ORDER_TOTALS_PROCESS'
#307: 'NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_TOTALS_PROCESS'
#319: 'NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_CREATE'
#326: 'NOTIFY_CHECKOUT_PROCESS_AFTER_PAYMENT_MODULES_AFTER_ORDER_CREATE'
#361: 'NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_CREATE_ADD_PRODUCTS'
#364: 'NOTIFY_CHECKOUT_PROCESS_AFTER_SEND_ORDER_EMAIL'
#398: 'NOTIFY_CHECKOUT_PROCESS_HANDLE_AFFILIATES', 'paypalipn'
#479: 'NOTIFY_PAYPALIPN_STATUS_HISTORY_UPDATE', array($ordersID, $new_status, $txn_type)

```

#### includes/classes/shopping_cart.php
```
#80: 'NOTIFIER_CART_INSTANTIATE_START'
#82: 'NOTIFIER_CART_INSTANTIATE_END'
#101: 'NOTIFIER_CART_RESTORE_CONTENTS_START'
#190: 'NOTIFIER_CART_RESTORE_CONTENTS_END'
#207: 'NOTIFIER_CART_RESET_START', array(), $reset_database
#234: 'NOTIFIER_CART_RESET_END'
#262: 'NOTIFIER_CART_ADD_CART_START', array(), $products_id, $qty, $attributes, $notify
#358: 'NOTIFIER_CART_ADD_CART_END'
#383: 'NOTIFIER_CART_UPDATE_QUANTITY_START', array(), $products_id, $quantity, $attributes
#467: 'NOTIFIER_CART_UPDATE_QUANTITY_END'
#482: 'NOTIFIER_CART_CLEANUP_START'
#502: 'NOTIFIER_CART_CLEANUP_END'
#516: 'NOTIFIER_CART_COUNT_CONTENTS_START'
#523: 'NOTIFIER_CART_COUNT_CONTENTS_END'
#536: 'NOTIFIER_CART_GET_QUANTITY_START', array(), $products_id
#538: 'NOTIFIER_CART_GET_QUANTITY_END_QTY', array(), $products_id
#541: 'NOTIFIER_CART_GET_QUANTITY_END_FALSE', $products_id
#552: 'NOTIFIER_CART_IN_CART_START', array(), $products_id
#554: 'NOTIFIER_CART_IN_CART_END_TRUE', array(), $products_id
#557: 'NOTIFIER_CART_IN_CART_END_FALSE', $products_id
#570: 'NOTIFIER_CART_REMOVE_START', array(), $products_id
#597: 'NOTIFIER_CART_REMOVE_END'
#605: 'NOTIFIER_CART_REMOVE_ALL_START'
#607: 'NOTIFIER_CART_REMOVE_ALL_END'
#662: 'NOTIFY_CART_CALCULATE_PRODUCT_PRICE', $products_id, $product->fields
#742: 'NOTIFY_CART_CALCULATE_ATTRIBUTE_PRICE', $products_id, $attribute_price->fields
#907: 'NOTIFY_CART_CALCULATE_ATTRIBUTE_WEIGHT', array('products_id' => $products_id, 'options_id' => $option), $attribute_weight->fields
#975: 'NOTIFY_CART_ATTRIBUTES_PRICE_START', $products_id
#994: 'NOTIFY_CART_ATTRIBUTES_PRICE_NEXT', $products_id, $attribute_price->fields
#1086: 'NOTIFY_CART_ATTRIBUTES_PRICE_ONETIME_CHARGES_START', $products_id
#1103: 'NOTIFY_CART_ATTRIBUTES_PRICE_ONETIME_CHARGES_NEXT', $products_id, $attribute_price->fields
#1164: 'NOTIFY_CART_ATTRIBUTES_WEIGHT_START', $products_id
#1179: 'NOTIFY_CART_ATTRIBUTES_WEIGHT_NEXT', $products_id, $attribute_weight_info->fields
#1212: 'NOTIFIER_CART_GET_PRODUCTS_START', array(), $check_for_valid_cart
#1230: 'NOTIFY_CART_GET_PRODUCTS_NEXT', $products_id, $products->fields
#1404: 'NOTIFIER_CART_GET_PRODUCTS_END', array(), $products_array
#1413: 'NOTIFIER_CART_SHOW_TOTAL_START'
#1415: 'NOTIFIER_CART_SHOW_TOTAL_END'
#1425: 'NOTIFIER_CART_SHOW_TOTAL_BEFORE_DISCOUNT_START'
#1427: 'NOTIFIER_CART_SHOW_TOTAL_BEFORE_DISCOUNT_END'
#2031: 'NOTIFIER_CART_OPTIONAL_ATTRIBUTE_ERROR_MESSAGE_HOOK', $_POST, $the_list
#2273: 'NOTIFY_CART_USER_ACTION', array(), $goto, $parameters

```

#### includes/classes/order.php
```
#45: 'NOTIFY_ORDER_INSTANTIATE', array(), $order_id
#58: 'NOTIFY_ORDER_BEFORE_QUERY', array(), $order_id
#258: 'NOTIFY_ORDER_QUERY_ADD_PRODUCT', $this->products[$index], $index
#264: 'NOTIFY_ORDER_AFTER_QUERY', IS_ADMIN_FLAG, $order_id
#270: 'ORDER_QUERY_ADMIN_COMPLETE', array('orders_id' => $order_id)
#467: 'NOTIFY_ORDER_CART_AFTER_ADDRESSES_SET', '', $taxCountryId, $taxZoneId
#515: 'NOTIFY_ORDER_CART_ADD_PRODUCT_LIST', array('index'=>$index, 'products'=>$products[$i])
#549: 'NOTIFY_ORDER_CART_ADD_ATTRIBUTE_LIST', array('index'=>$index, 'subindex'=>$subindex, 'products'=>$products[$i], 'attributes'=>$attributes)
#561: 'NOTIFY_ORDER_CART_EXTERNAL_TAX_HANDLING', array(), $index, $taxCountryId, $taxZoneId
#570: 'NOTIFIY_ORDER_CART_SUBTOTAL_CALCULATE', array('shown_price'=>$shown_price)
#615: 'NOTIFY_ORDER_CART_FINISHED'
#621: 'NOTIFY_ORDER_CART_EXTERNAL_TAX_DURING_ORDER_CREATE', array(), $zf_ot_modules
#632: 'NOTIFY_ORDER_CART_ORDERSTATUS'
#696: 'NOTIFY_ORDER_DURING_CREATE_ADDED_ORDER_HEADER', array_merge(array('orders_id' => $insert_id, 'shipping_weight' => $_SESSION['cart']->weight), $sql_data_array), $insert_id
#708: 'NOTIFY_ORDER_DURING_CREATE_ADDED_ORDERTOTAL_LINE_ITEM', $sql_data_array, $ot_insert_id
#720: 'NOTIFY_ORDER_DURING_CREATE_ADDED_ORDER_COMMENT', $sql_data_array, $osh_insert_id
#743: 'NOTIFY_ORDER_PROCESSING_STOCK_DECREMENT_INIT', array('i'=>$i), $this->products[$i], $i
#766: 'NOTIFY_ORDER_PROCESSING_STOCK_DECREMENT_BEGIN', $i, $stock_values
#798: 'NOTIFY_ORDER_PROCESSING_BESTSELLERS_UPDATE', array(), $this->products[$i], $i
#803: 'NOTIFY_ORDER_PROCESSING_STOCK_DECREMENT_END', $i
#832: 'NOTIFY_ORDER_DURING_CREATE_ADDED_PRODUCT_LINE_ITEM', array_merge(array('orders_products_id' => $order_products_id, 'i' => $i), $sql_data_array), $order_products_id
#834: 'NOTIFY_ORDER_PROCESSING_CREDIT_ACCOUNT_UPDATE_BEGIN'
#837: 'NOTIFY_ORDER_PROCESSING_ATTRIBUTES_BEGIN'
#915: 'NOTIFY_ORDER_DURING_CREATE_ADDED_ATTRIBUTE_LINE_ITEM', array_merge(array('orders_products_attributes_id' => $opa_insert_id), $sql_data_array), $opa_insert_id
#929: 'NOTIFY_ORDER_DURING_CREATE_ADDED_ATTRIBUTE_DOWNLOAD_LINE_ITEM', $sql_data_array, $opd_insert_id
#935: 'NOTIFY_ORDER_PROCESSING_ATTRIBUTES_EXIST', $attributes_exist
#937: 'NOTIFY_ORDER_DURING_CREATE_ADD_PRODUCTS', $i, $custom_insertable_text
#965: 'NOTIFY_ORDER_PROCESSING_ONE_TIME_CHARGES_BEGIN', $i
#989: 'NOTIFY_ORDER_AFTER_ORDER_CREATE_ADD_PRODUCTS'
#995: 'NOTIFY_ORDER_SEND_EMAIL_INITIALIZE', array(), $zf_insert_id, $order_totals, $zf_mode
#999: 'NOTIFY_ORDER_SEND_LOW_STOCK_EMAILS'
#1044: 'NOTIFY_ORDER_EMAIL_BEFORE_PRODUCTS', array(), $email_order, $html_msg
#1108: 'NOTIFY_ORDER_SET_ORDER_MESSAGE'
#1126: 'NOTIFY_ORDER_INVOICE_CONTENT_READY_TO_SEND', array('zf_insert_id' => $zf_insert_id, 'text_email' => $email_order, 'html_email' => $html_msg), $email_order, $html_msg
#1145: 'NOTIFY_ORDER_INVOICE_CONTENT_FOR_ADDITIONAL_EMAILS', $zf_insert_id, $email_order, $html_msg
#1152: 'NOTIFY_ORDER_AFTER_SEND_ORDER_EMAIL', $zf_insert_id, $email_order, $extra_info, $html_msg

```

#### includes/classes/shipping.php
```
#58: 'NOTIFY_SHIPPING_MODULE_ENABLE', $include_modules[$i]['class'], $include_modules[$i]['class']
#77: 'NOTIFY_SHIPPING_CHECK_ENABLED_FOR_ZONE', array(), $class, $enabled
#82: 'NOTIFY_SHIPPING_CHECK_ENABLED', array(), $class, $enabled
#89: 'NOTIFY_SHIPPING_MODULE_PRE_CALCULATE_BOXES_AND_TARE', array(), $total_weight, $shipping_weight, $shipping_quoted, $shipping_num_boxes
#137: 'NOTIFY_SHIPPING_MODULE_CALCULATE_BOXES_AND_TARE', array(), $total_weight, $shipping_weight, $shipping_quoted, $shipping_num_boxes
#173: 'NOTIFY_SHIPPING_MODULE_GET_ALL_QUOTES', $quotes_array, $quotes_array
#215: 'NOTIFY_SHIPPING_MODULE_CALCULATE_CHEAPEST', $cheapest, $cheapest, $rates

```

#### includes/classes/payment.php
```
#75: 'NOTIFY_PAYMENT_MODULE_ENABLE'

```

#### includes/classes/observers/auto.downloads_via_streaming.php
```
#42: 'NOTIFY_DOWNLOAD_WITHOUT_REDIRECT___COMPLETED', $origin_filename
#54: 'NOTIFY_DOWNLOAD_IN_CHUNKS___COMPLETED', $origin_filename
#77: 'NOTIFY_DOWNLOAD_WITHOUT_REDIRECT_VIA_CHUNKS___COMPLETED'

```

#### includes/classes/observers/auto.downloads_via_redirect.php
```
#78: 'NOTIFY_DOWNLOAD_VIA_SYMLINK___BEGINS', array($download_link, $origin_filename, $tempdir)

```

#### includes/init_includes/init_languages.php
```
#18: 'NOTIFY_LANGUAGE_CHANGE_REQUESTED_BY_VISITOR', $_GET['language'], $lng

```

#### includes/init_includes/init_canonical.php
```
#41: 'NOTIFY_INIT_CANONICAL_PARAM_WHITELIST', $current_page, $excludeParams, $keepableParams, $includeCPath
#118: 'NOTIFY_INIT_CANONICAL_DEFAULT', $current_page, $excludeParams, $canonicalLink
#120: 'NOTIFY_INIT_CANONICAL_FINAL', $current_page, $excludeParams, $canonicalLink

```

#### includes/init_includes/init_customer_auth.php
```
#58: 'NOTIFY_LOGIN_BANNED'

```

#### includes/functions/html_output.php
```
#18: 'NOTIFY_SEFU_INTERCEPT', array(), $link, $page, $parameters, $connection, $add_session_id, $static, $use_dir_ws_catalog
#203: 'NOTIFY_HANDLE_IMAGE', array($newimg)
#283: 'PAGE_OUTPUT_IMAGE_SUBMIT'
#307: 'PAGE_OUTPUT_IMAGE_BUTTON'
#359:  'NOTIFY_ZEN_CSS_BUTTON_SUBMIT', array( 'button_name' => $button_name, 'text' => $text, 'sec_class' => $sec_class, 'parameters' => $parameters, ), $css_button 
#381:  'NOTIFY_ZEN_CSS_BUTTON_BUTTON', array( 'button_name' => $button_name, 'text' => $text, 'sec_class' => $sec_class, 'parameters' => $parameters, ), $css_button 
#436:  'NOTIFY_ZEN_DRAW_INPUT_FIELD_OVERRIDE', array( 'name' => $name, 'value' => $value, 'parameters' => $parameters, 'type' => $type, 'reinsert_value' => $reinsert_value ), $field 
#465:  'NOTIFY_ZEN_DRAW_INPUT_FIELD', array( 'name' => $name, 'value' => $value, 'parameters' => $parameters, 'type' => $type, 'reinsert_value' => $reinsert_value ), $field 
#494:  'NOTIFY_ZEN_DRAW_SELECTION_FIELD_OVERRIDE', array( 'name' => $name, 'value' => $value, 'parameters' => $parameters, 'type' => $type, 'checked' => $checked ), $selection 
#524:  'NOTIFY_ZEN_DRAW_SELECTION_FIELD', array( 'name' => $name, 'value' => $value, 'parameters' => $parameters, 'type' => $type, 'checked' => $checked ), $selection 
#560:  'NOTIFY_ZEN_DRAW_TEXTAREA_FIELD_OVERRIDE', array( 'name' => $name, 'width' => $width, 'height' => $height, 'text' => $text, 'parameters' => $parameters, 'reinsert_value' => $reinsert_value, ), $field 
#593:  'NOTIFY_ZEN_DRAW_TEXTAREA_FIELD', array( 'name' => $name, 'width' => $width, 'height' => $height, 'text' => $text, 'parameters' => $parameters, 'reinsert_value' => $reinsert_value, ), $field 
#658:  'NOTIFY_ZEN_DRAW_PULL_DOWN_MENU_OVERRIDE', array( 'name' => $name, 'values' => $values, 'default' => $default, 'parameters' => $parameters, 'required' => $required, ), $field 
#700:  'NOTIFY_ZEN_DRAW_PULL_DOWN_MENU', array( 'name' => $name, 'values' => $values, 'default' => $default, 'parameters' => $parameters, 'required' => $required, ), $field 

```

#### includes/functions/functions_prices.php
```
#131: 'ZEN_GET_PRODUCTS_BASE_PRICE', $products_id, $products_base_price, $base_price_is_handled
#237:  'NOTIFY_ZEN_GET_PRODUCTS_DISPLAY_PRICE_SALE', array( 'products_id' => $products_id, 'display_sale_price' => $display_sale_price, 'display_special_price' => $display_special_price, 'display_normal_price' => $display_normal_price, 'products_tax_class_id' => $product_check->fields['products_tax_class_id'] ), $pricing_handled, $show_sale_discount 
#277:  'NOTIFY_ZEN_GET_PRODUCTS_DISPLAY_PRICE_SPECIAL', array( 'products_id' => $products_id, 'display_sale_price' => $display_sale_price, 'display_special_price' => $display_special_price, 'display_normal_price' => $display_normal_price, 'products_tax_class_id' => $product_check->fields['products_tax_class_id'], 'product_is_free' => $product_check->fields['product_is_free'] ), $pricing_handled, $show_normal_price, $show_special_price, $show_sale_price 
#315:  'NOTIFY_ZEN_GET_PRODUCTS_DISPLAY_PRICE_NORMAL', array( 'products_id' => $products_id, 'display_sale_price' => $display_sale_price, 'display_special_price' => $display_special_price, 'display_normal_price' => $display_normal_price, 'products_tax_class_id' => $product_check->fields['products_tax_class_id'], 'product_is_free' => $product_check->fields['product_is_free'] ), $pricing_handled, $show_normal_price, $show_special_price, $show_sale_price 
#358:  'NOTIFY_ZEN_GET_PRODUCTS_DISPLAY_PRICE_FREE_OR_CALL', array( 'product_is_free' => $product_check->fields['product_is_free'], 'product_is_call' => $product_check->fields['product_is_call'], ), $tags_handled, $free_tag, $call_tag 

```

#### includes/functions/functions_osh_update.php
```
#71: 'ZEN_UPDATE_ORDERS_HISTORY_PRE_EMAIL', array('message' => $message), $osh_additional_comments
#89: 'ZEN_UPDATE_ORDERS_HISTORY_STATUS_VALUES', array('orders_id' => $orders_id, 'new' => $orders_new_status, 'old' => $orders_current_status)
#183: 'ZEN_UPDATE_ORDERS_HISTORY_BEFORE_INSERT', array(), $osh_sql

```

#### includes/functions/functions_customers.php
```
#96:  'NOTIFY_END_ZEN_ADDRESS_FORMAT', array( 'format' => $fmt, 'address' => $incoming, 'firstname' => $address['$firstname'], 'lastname' => $address['$lastname'], 'street' => $address['$street'], 'suburb' => $address['$suburb'], 'city' => $address['$city'], 'state' => $address['$state'], 'country' => $address['$country'], 'postcode' => $address['$postcode'], 'company' => $address['$company'], 'streets' => $address['$streets'], 'statecomma' => $address['$statecomma'], 'zip' => $address['$zip'], 'cr' => $address['$cr'], 'hr' => $address['$hr'], ), $address_out 
#138: 'NOTIFY_ZEN_ADDRESS_LABEL', array(), $customers_id, $address_id, $address->fields
#247: 'NOTIFY_ZEN_IN_GUEST_CHECKOUT', '', $in_guest_checkout
#257: 'NOTIFY_ZEN_IS_LOGGED_IN', '', $is_logged_in

```

#### includes/functions/functions_lookups.php
```
#165:  'ZEN_GET_PRODUCTS_STOCK', $products_id, $products_quantity, $quantity_handled 
#200:  'ZEN_CHECK_STOCK_MESSAGE', array( $products_id, $products_quantity ), $out_of_stock_message 
#304: 'FUNCTIONS_LOOKUPS_OPTION_NAME_NO_VALUES_OPT_TYPE', $opt_type, $test_var
#325: 'NOTIFY_ZEN_HAS_PRODUCT_ATTRIBUTES_VALUES', $products_id, $value_to_return

```

#### includes/functions/functions_taxes.php
```
#20:  'NOTIFY_ZEN_GET_TAX_RATE_OVERRIDE', array( 'class_id' => $class_id, 'country_id' => $country_id, 'zone_id' => $zone_id ), $tax_rate 
#84:  'NOTIFY_ZEN_GET_TAX_DESCRIPTION_OVERRIDE', array( 'class_id' => $class_id, 'country_id' => $country_id, 'zone_id' => $zone_id ), $tax_description 
#143:  'NOTIFY_ZEN_GET_MULTIPLE_TAX_RATES_OVERRIDE', array( 'class_id' => $class_id, 'country_id' => $country_id, 'zone_id' => $zone_id, 'tax_description' => $tax_description ), $rates_array 
#285:  'ZEN_GET_TAX_LOCATIONS', array( 'country' => $store_country, 'zone' => $store_zone ), $tax_address 
#348:  'NOTIFY_ZEN_GET_ALL_TAX_DESCRIPTIONS_OVERRIDE', array( 'country_id' => $country_id, 'zone_id' => $zone_id ), $tax_descriptions 

```

#### includes/functions/functions_email.php
```
#93: 'NOTIFY_EMAIL_ADDRESS_TEST', array(), $to_name, $to_email_address, $email_subject
#96: 'NOTIFY_EMAIL_ADDRESS_VALIDATION_FAILURE', sprintf(EMAIL_SEND_FAILED . ' (failed validation)', $to_name, $to_email_address, $email_subject)
#182: 'NOTIFY_EMAIL_AFTER_EMAIL_FORMAT_DETERMINED'
#273: 'NOTIFY_EMAIL_BEFORE_PROCESS_ATTACHMENTS', array('attachments'=>$attachments_list, 'module'=>$module)
#303: 'NOTIFY_EMAIL_AFTER_PROCESS_ATTACHMENTS', sizeof($attachments_list)
#344: 'NOTIFY_EMAIL_READY_TO_SEND', array($mail), $mail
#361: 'NOTIFY_EMAIL_AFTER_SEND'
#366: 'NOTIFY_EMAIL_AFTER_SEND_WITH_ALL_PARAMS', array($to_name, $to_email_address, $from_email_name, $from_email_address, $email_subject, $email_html, $text, $module, $ErrorInfo)
#373: 'NOTIFY_EMAIL_AFTER_SEND_ALL_SPECIFIED_ADDRESSES'
#400: 'NOTIFY_EMAIL_BEGIN_ARCHIVE_WRITE', array($to_name, $to_email_address, $from_email_name, $from_email_address, $email_subject, $email_html, $email_text, $module, $error_msgs)
#709: 'NOTIFY_EMAIL_VALIDATION_TEST', array($email, $valid_address)

```

#### includes/templates/responsive_classic/common/tpl_columnar_display.php
```
#13: 'NOTIFY_TPL_COLUMNAR_DISPLAY_START', $current_page_base, $list_box_contents, $title
#46: 'NOTIFY_TPL_COLUMNAR_DISPLAY_END', $current_page_base, $list_box_contents, $title

```

#### includes/templates/responsive_classic/common/main_template_vars.php
```
#17: 'NOTIFY_MAIN_TEMPLATE_VARS_START', $template_dir
#49: 'NOTIFY_MAIN_TEMPLATE_VARS_END', $template_dir, $body_code

```

#### includes/templates/responsive_classic/common/html_header.php
```
#13: 'NOTIFY_HTML_HEAD_START', $current_page_base, $template_dir
#210: 'NOTIFY_HTML_HEAD_END', $current_page_base

```

#### includes/templates/responsive_classic/common/tpl_main_page.php
```
#268: 'NOTIFY_FOOTER_END', $current_page

```

#### includes/templates/responsive_classic/common/tpl_tabular_display.php
```
#13: 'NOTIFY_TPL_TABULAR_DISPLAY_START', $current_page_base, $list_box_contents
#50: 'NOTIFY_TPL_TABULAR_DISPLAY_END', $current_page_base, $list_box_contents

```

#### includes/templates/template_default/common/tpl_columnar_display.php
```
#13: 'NOTIFY_TPL_COLUMNAR_DISPLAY_START', $current_page_base, $list_box_contents, $title
#46: 'NOTIFY_TPL_COLUMNAR_DISPLAY_END', $current_page_base, $list_box_contents, $title

```

#### includes/templates/template_default/common/main_template_vars.php
```
#17: 'NOTIFY_MAIN_TEMPLATE_VARS_START', $template_dir
#35: 'NOTIFY_MAIN_TEMPLATE_VARS_END', $template_dir, $body_code

```

#### includes/templates/template_default/common/html_header.php
```
#13: 'NOTIFY_HTML_HEAD_START', $current_page_base, $template_dir
#164: 'NOTIFY_HTML_HEAD_END', $current_page_base

```

#### includes/templates/template_default/common/tpl_main_page.php
```
#200: 'NOTIFY_FOOTER_END', $current_page

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

#### includes/modules/responsive_classic/product_listing.php
```
#15: 'NOTIFY_MODULE_PRODUCT_LISTING_RESULTCOUNT', $listing_split->number_of_rows
#211: 'NOTIFY_PRODUCT_LISTING_END', $current_page_base, $list_box_contents, $listing_split, $show_top_submit_button, $show_bottom_submit_button, $show_submit, $how_many

```

#### includes/modules/checkout_new_address.php
```
#11: 'NOTIFY_MODULE_START_CHECKOUT_NEW_ADDRESS'
#135: 'NOTIFY_MODULE_CHECKOUT_NEW_ADDRESS_VALIDATION', array(), $error
#161: 'NOTIFY_MODULE_CHECKOUT_ADDED_ADDRESS_BOOK_RECORD', array_merge(array('address_id' => $address_book_id ), $sql_data_array)
#255: 'NOTIFY_MODULE_END_CHECKOUT_NEW_ADDRESS'

```

#### includes/modules/meta_tags.php
```
#16: 'NOTIFY_MODULE_START_META_TAGS', $current_page_base, $metatag_page_name, $meta_tags_over_ride
#35: 'NOTIFY_MODULE_META_TAGS_BUILDKEYWORDS', CUSTOM_KEYWORDS, $keywords_string_metatags
#330: 'NOTIFY_MODULE_META_TAGS_UNSPECIFIEDPAGE', $current_page_base, $metatag_page_name, $meta_tags_over_ride, $metatags_title, $metatags_description, $metatags_keywords
#338: 'NOTIFY_MODULE_META_TAGS_OVERRIDE', $metatag_page_name, $meta_tags_over_ride, $metatags_title, $metatags_description, $metatags_keywords
#348: 'NOTIFY_MODULE_END_META_TAGS'

```

#### includes/modules/attributes.php
```
#101: 'NOTIFY_ATTRIBUTES_MODULE_START_OPTION', $products_options_names->fields
#116: 'NOTIFY_ATTRIBUTES_MODULE_START_OPTIONS_LOOP', $i++, $products_options->fields
#471: 'NOTIFY_ATTRIBUTES_MODULE_FORMAT_VALUE', $products_options->fields
#611: 'NOTIFY_ATTRIBUTES_MODULE_DEFAULT_SWITCH', $products_options_names->fields, $options_name, $options_menu, $options_comment, $options_comment_position, $options_html_id
#618: 'NOTIFY_ATTRIBUTES_MODULE_OPTION_BUILT', $products_options_names->fields, $options_name, $options_menu, $options_comment, $options_comment_position, $options_html_id, $options_attributes_image

```

#### includes/modules/create_account.php
```
#11: 'NOTIFY_MODULE_START_CREATE_ACCOUNT'
#40: 'NOTIFY_CREATE_ACCOUNT_CAPTCHA_CHECK'
#147: 'NOTIFY_CREATE_ACCOUNT_LOOKUP_BY_EMAIL', $email_address, $check_email_query, $send_welcome_email
#155: 'NOTIFY_NICK_CHECK_FOR_EXISTING_EMAIL', $email_address, $nick_error, $nick
#165: 'NOTIFY_NICK_CHECK_FOR_MIN_LENGTH', $nick, $nick_error, $nick_length_min
#167: 'NOTIFY_NICK_CHECK_FOR_DUPLICATE', $nick, $nick_error
#257: 'NOTIFY_CREATE_ACCOUNT_VALIDATION_CHECK', array(), $error, $send_welcome_email
#269: 'NOTIFY_FAILURE_DURING_CREATE_ACCOUNT'
#271: 'NOTIFY_SPAM_DETECTED_DURING_CREATE_ACCOUNT'
#296: 'NOTIFY_MODULE_CREATE_ACCOUNT_ADDED_CUSTOMER_RECORD', array_merge(array('customer_id' => $_SESSION['customer_id']), $sql_data_array)
#326: 'NOTIFY_MODULE_CREATE_ACCOUNT_ADDED_ADDRESS_BOOK_RECORD', array_merge(array('address_id' => $address_id), $sql_data_array)
#343: 'NOTIFY_NICK_CREATE_NEW', $nick, $password, $nick_email, $extra_welcome_text
#360: 'NOTIFY_LOGIN_SUCCESS_VIA_CREATE_ACCOUNT', $email_address, $extra_welcome_text, $send_welcome_email
#466: 'NOTIFY_NICK_SET_TEMPLATE_FLAG', 0, $display_nick_field
#470: 'NOTIFY_MODULE_END_CREATE_ACCOUNT'

```

#### includes/modules/payment/payeezyjszc.php
```
#638: 'NOTIFY_CHECKOUT_SLAMMING_LOCKOUT', $response

```

#### includes/modules/payment/authorizenet.php
```
#347: 'NOTIFY_PAYMENT_AUTHNETSIM_PRESUBMIT_HOOK'
#420: 'NOTIFY_PAYMENT_AUTHNETSIM_POSTSUBMIT_HOOK', $this->authorize
#459: 'NOTIFY_PAYMENT_AUTHNETSIM_POSTPROCESS_HOOK'

```

#### includes/modules/payment/paypaldp.php
```
#1099: 'NOTIFY_PAYMENT_PAYPALDP_INSTALLED'
#1115: 'NOTIFY_PAYMENT_PAYPALDP_UNINSTALLED'
#1521: 'NOTIFY_PAYMENT_PAYPALDP_SUBTOTALS_REVIEW', $order, $order_totals

```

#### includes/modules/payment/paypalwpp.php
```
#419: 'NOTIFY_PAYPALWPP_BEFORE_DOEXPRESSCHECKOUT'
#467: 'NOTIFY_PAYPALWPP_BEFORE_PROCESS_FINISHED', $response
#546: 'NOTIFY_PAYPALWPP_AFTER_PROCESS_FINISHED', $paypal_order
#701: 'NOTIFY_PAYMENT_PAYPALWPP_INSTALLED'
#744: 'NOTIFY_PAYMENT_PAYPALWPP_UNINSTALLED'
#1273: 'NOTIFY_PAYMENT_PAYPALEC_SUBTOTALS_TAX', $order, $order_totals
#1365: 'NOTIFY_PAYPALWPP_GETLINEITEMDETAILS', $numberOfLineItemsProcessed, $optionsLI
#1686: 'NOTIFY_PAYMENT_PAYPALEC_BEFORE_SETEC', array(), $options, $order, $order_totals
#1694: 'NOTIFY_PAYMENT_PAYPALEC_TOKEN', $response, $options
#1809: 'NOTIFY_PAYPALEC_PARSE_GETEC_RESULT', array(), $response
#1829: 'NOTIFY_PAYPAL_EXPRESS_CHECKOUT_PAYERID_DETERMINED', $response['PAYERID']
#1949: 'NOTIFY_PAYPAL_CUSTOMER_ATTEMPT_TO_USE_INVALID_COUNTRY_CODE'
#2037: 'NOTIFY_PAYPALEXPRESS_BYPASS_ADDRESS_CREATION', $paypal_ec_payer_info, $bypass_address_creation
#2147: 'NOTIFY_PAYPALEXPRESS_CREATE_ACCOUNT_ADDED_CUSTOMER_RECORD', $customer_id, $sql_data_array
#2178: 'NOTIFY_PAYPALEXPRESS_CREATE_ACCOUNT_ADDED_ADDRESS_BOOK_RECORD', array(), $address_id, $sql_data_array
#2231: 'NOTIFY_LOGIN_SUCCESS_VIA_CREATE_ACCOUNT', 'paypal express checkout'
#2272: 'NOTIFY_PAYPALEC_END_ECSTEP2', $order
#2590: 'NOTIFY_HEADER_ADDRESS_BOOK_ADD_ENTRY_INVALID_ATTEMPT', $customer_id, $country_id, $address_format_id, $address_question_arr
#2651: 'NOTIFY_HEADER_ADDRESS_BOOK_ADD_ENTRY_DONE', 'paypal express checkout', $new_address_book_id, $sql_data_array, $make_default
#2895: 'NOTIFY_PAYPALWPP_ERROR_HANDLER', $response, $operation, $basicError, $ignoreList, $errorInfo

```

#### includes/modules/payment/firstdata_hco.php
```
#295: 'MODULE_PAYMENT_FIRSTDATA_PAYMENTPAGES_PRESUBMIT_HOOK'
#348: 'MODULE_PAYMENT_FIRSTDATA_PAYMENTPAGES_POSTSUBMIT_HOOK', $this->authorize
#382: 'MODULE_PAYMENT_FIRSTDATA_PAYMENTPAGES_POSTPROCESS_HOOK'

```

#### includes/modules/payment/paypal/paypal_curl.php
```
#109: 'NOTIFY_PAYPAL_CURL_CONSTRUCT', $params
#156: 'NOTIFY_PAYPAL_SETEXPRESSCHECKOUT'
#172: 'NOTIFY_PAYPAL_GETEXPRESSCHECKOUTDETAILS'
#196: 'NOTIFY_PAYPAL_DOEXPRESSCHECKOUTPAYMENT'
#239: 'NOTIFY_PAYPAL_DODIRECTPAYMENT'
#561: 'NOTIFY_PAYPAL_CURL_BUILDNAMEVALUELIST', $string
#662: 'PAYPAL_CURL_LOG', $token, $tokenHash

```

#### includes/modules/payment/authorizenet_aim.php
```
#400: 'NOTIFY_PAYMENT_AUTHNET_EMULATOR_CHECK', $this->code, $submit_data
#415: 'NOTIFY_PAYMENT_AUTHNET_PRESUBMIT_HOOK', $this->code, $submit_data
#421: 'NOTIFY_PAYMENT_AUTHNET_POSTSUBMIT_HOOK', $this->code, $response
#607: 'NOTIFY_PAYMENT_AUTHNET_MODE_SELECTION', $this->mode, $submit_data
#687: 'NOTIFY_PAYMENT_AUTHNET_ENCAPSULATION_CHECK'

```

#### includes/modules/payment/paypal.php
```
#356: 'NOTIFY_PAYMENT_PAYPAL_RETURN_TO_STORE', $_GET
#381: 'NOTIFY_PAYMENT_PAYPAL_CANCELLED_DURING_CHECKOUT', $_GET
#534: 'NOTIFY_PAYMENT_PAYPAL_INSTALLED'
#543: 'NOTIFY_PAYMENT_PAYPAL_UNINSTALLED'

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
#15: 'NOTIFY_MODULES_ADDITIONAL_PRODUCT_IMAGES_START'
#55:  'NOTIFY_MODULES_ADDITIONAL_IMAGES_FILE_MATCH', array( 'file' => $file, 'file_extension' => $file_extension, 'products_image' => $products_image, 'products_image_base' => $products_image_base ), $current_image_match 
#86: 'NOTIFY_MODULES_ADDITIONAL_PRODUCT_IMAGES_LIST', NULL, $images_array
#113: 'NOTIFY_MODULES_ADDITIONAL_IMAGES_GET_LARGE', $products_name, $products_image_large
#128: 'NOTIFY_MODULES_ADDITIONAL_IMAGES_THUMB_SLASHES', array(), $thumb_slashes
#147:  'NOTIFY_MODULES_ADDITIONAL_IMAGES_SCRIPT_LINK', array( 'flag_display_large' => $flag_display_large, 'products_name' => $products_name, 'products_image_large' => $products_image_large, 'thumb_slashes' => $thumb_slashes, 'index' => $i ), $script_link, $link_parameters 
#183: 'NOTIFY_MODULES_ADDITIONAL_PRODUCT_IMAGES_END'

```

#### includes/modules/checkout_address_book.php
```
#26: 'NOTIFY_MODULE_END_CHECKOUT_ADDRESS_BOOK', $addresses_query, $addresses

```

#### includes/modules/sideboxes/ezpages.php
```
#11: 'NOTIFY_START_EZPAGES_SIDEBOX'
#72: 'NOTIFY_END_EZPAGES_SIDEBOX'
#77: 'NOTIFY_END_EZPAGES_SIDEBOX'

```

#### includes/modules/ezpages_bar_header.php
```
#13: 'NOTIFY_START_EZPAGES_HEADERBAR'
#67: 'NOTIFY_END_EZPAGES_HEADERBAR'

```

#### includes/modules/checkout_process.php
```
#13: 'NOTIFY_CHECKOUT_PROCESS_BEGIN'
#32: 'NOTIFY_CHECKOUT_SLAMMING_ALERT', $_SESSION['payment_attempt'], $slamming_threshold
#34: 'NOTIFY_CHECKOUT_SLAMMING_LOCKOUT'
#74: 'NOTIFY_CHECKOUT_PROCESS_BEFORE_ORDER_TOTALS_PRE_CONFIRMATION_CHECK'
#82: 'NOTIFY_CHECKOUT_PROCESS_BEFORE_ORDER_TOTALS_PROCESS'
#84: 'NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_TOTALS_PROCESS'
#92: 'NOTIFY_CHECKOUT_PROCESS_AFTER_PAYMENT_MODULES_BEFOREPROCESS'
#95: 'NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_CREATE'
#97: 'NOTIFY_CHECKOUT_PROCESS_AFTER_PAYMENT_MODULES_AFTER_ORDER_CREATE'
#101: 'NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_CREATE_ADD_PRODUCTS'
#104: 'NOTIFY_CHECKOUT_PROCESS_AFTER_SEND_ORDER_EMAIL'
#144: 'NOTIFY_CHECKOUT_PROCESS_HANDLE_AFFILIATES'

```

#### includes/modules/ezpages_bar_footer.php
```
#13: 'NOTIFY_START_EZPAGES_FOOTERBAR'
#67: 'NOTIFY_END_EZPAGES_FOOTERBAR'

```

#### includes/modules/product_listing.php
```
#15: 'NOTIFY_MODULE_PRODUCT_LISTING_RESULTCOUNT', $listing_split->number_of_rows
#142: 'NOTIFY_MODULES_PRODUCT_LISTING_PRODUCTS_BUTTON', array(), $listing->fields, $lc_button
#224: 'NOTIFY_PRODUCT_LISTING_END', $current_page_base, $list_box_contents, $listing_split, $show_top_submit_button, $show_bottom_submit_button, $show_submit, $how_many

```

#### includes/modules/order_total/ot_shipping.php
```
#51:  'NOTIFY_OT_SHIPPING_TAX_CALCS', array(), $external_shipping_tax_handler, $shipping_tax, $shipping_tax_description 

```

#### includes/modules/order_total/ot_coupon.php
```
#167:  'NOTIFY_OT_COUPON_COUPON_REMOVED' 
#205:  'NOTIFY_OT_COUPON_COUPON_INFO', array( 'coupon_result' => $coupon_result->fields, 'code' => $dc_check ) 
#324: 'NOTIFY_OT_COUPON_USES_PER_USER_CHECK', $coupon_result->fields, $coupon_uses_per_user_exceeded
#611:  'NOTIFY_OT_COUPON_PRODUCT_VALIDITY', array( 'is_product_valid' => $is_product_valid, 'i' => $i ) 

```

#### includes/modules/new_products.php
```
#70: 'NOTIFY_MODULES_NEW_PRODUCTS_B4_LIST_BOX', array(), $new_products->fields, $products_price

```

#### includes/modules/pages/page/header_php.php
```
#19: 'NOTIFY_HEADER_START_EZPAGE'
#191: 'NOTIFY_HEADER_END_EZPAGE'

```

#### includes/modules/pages/checkout_success/header_php.php
```
#12: 'NOTIFY_HEADER_START_CHECKOUT_SUCCESS'
#174: 'NOTIFY_HEADER_END_CHECKOUT_SUCCESS'

```

#### includes/modules/pages/create_account_success/header_php.php
```
#12: 'NOTIFY_HEADER_START_CREATE_ACCOUNT_SUCCESS'
#65: 'NOTIFY_HEADER_END_CREATE_ACCOUNT_SUCCESS'

```

#### includes/modules/pages/account_history_info/header_php.php
```
#11: 'NOTIFY_HEADER_START_ACCOUNT_HISTORY_INFO'
#65: 'NOTIFY_HEADER_END_ACCOUNT_HISTORY_INFO'

```

#### includes/modules/pages/product_free_shipping_info/main_template_vars.php
```
#15: 'NOTIFY_MAIN_TEMPLATE_VARS_START_PRODUCT_FREE_SHIPPING_INFO'
#36: 'NOTIFY_PRODUCT_VIEWS_HIT_INCREMENTOR', (int)$_GET['products_id']
#134: 'NOTIFY_MAIN_TEMPLATE_VARS_PRODUCT_TYPE_VARS_PRODUCT_FREE_SHIPPING_INFO'
#173: 'NOTIFY_MAIN_TEMPLATE_VARS_EXTRA_PRODUCT_FREE_SHIPPING_INFO'
#181: 'NOTIFY_MAIN_TEMPLATE_VARS_END_PRODUCT_FREE_SHIPPING_INFO'

```

#### includes/modules/pages/product_free_shipping_info/main_template_vars_product_type.php
```
#18: 'NOTIFY_PRODUCT_TYPE_VARS_START_PRODUCT_FREE_SHIPPING_INFO'
#36: 'NOTIFY_PRODUCT_TYPE_VARS_END_PRODUCT_FREE_SHIPPING_INFO'

```

#### includes/modules/pages/account_history/header_php.php
```
#11: 'NOTIFY_HEADER_START_ACCOUNT_HISTORY'
#68: 'NOTIFY_HEADER_END_ACCOUNT_HISTORY'

```

#### includes/modules/pages/checkout_payment/header_php.php
```
#12: 'NOTIFY_HEADER_START_CHECKOUT_PAYMENT'
#123: 'NOTIFY_HEADER_END_CHECKOUT_PAYMENT'

```

#### includes/modules/pages/document_general_info/main_template_vars.php
```
#15: 'NOTIFY_MAIN_TEMPLATE_VARS_START_DOCUMENT_GENERAL_INFO'
#36: 'NOTIFY_PRODUCT_VIEWS_HIT_INCREMENTOR', (int)$_GET['products_id']
#134: 'NOTIFY_MAIN_TEMPLATE_VARS_PRODUCT_TYPE_VARS_DOCUMENT_GENERAL_INFO'
#173: 'NOTIFY_MAIN_TEMPLATE_VARS_EXTRA_DOCUMENT_GENERAL_INFO'
#181: 'NOTIFY_MAIN_TEMPLATE_VARS_END_DOCUMENT_GENERAL_INFO'

```

#### includes/modules/pages/document_general_info/header_php.php
```
#12: 'NOTIFY_HEADER_START_DOCUMENT_GENERAL_INFO'
#17: 'NOTIFY_HEADER_END_DOCUMENT_GENERAL_INFO'

```

#### includes/modules/pages/document_general_info/main_template_vars_product_type.php
```
#18: 'NOTIFY_PRODUCT_TYPE_VARS_START_DOCUMENT_GENERAL_INFO'
#36: 'NOTIFY_PRODUCT_TYPE_VARS_END_DOCUMENT_GENERAL_INFO'

```

#### includes/modules/pages/checkout_confirmation/header_php.php
```
#12: 'NOTIFY_HEADER_START_CHECKOUT_CONFIRMATION'
#170: 'NOTIFY_HEADER_END_CHECKOUT_CONFIRMATION'

```

#### includes/modules/pages/product_reviews/header_php.php
```
#12: 'NOTIFY_HEADER_START_PRODUCT_REVIEWS'
#87: 'NOTIFY_HEADER_END_PRODUCT_REVIEWS'

```

#### includes/modules/pages/contact_us/header_php.php
```
#12: 'NOTIFY_HEADER_START_CONTACT_US'
#26: 'NOTIFY_CONTACT_US_CAPTCHA_CHECK', $_POST
#33: 'NOTIFY_SPAM_DETECTED_USING_CONTACT_US', $_POST
#51: 'NOTIFY_CONTACT_US_ACTION', (isset($_SESSION['customer_id']) ? $_SESSION['customer_id'] : 0), $customer_email, $customer_name, $email_address, $name, $enquiry
#139: 'NOTIFY_HEADER_END_CONTACT_US'

```

#### includes/modules/pages/featured_products/header_php.php
```
#12: 'NOTIFY_HEADER_START_FEATURED_PRODUCTS'
#37: 'NOTIFY_FEATURED_PRODUCTS_SQL_STRING', array(), $featured_products_query_raw
#84: 'NOTIFY_HEADER_END_FEATURED_PRODUCTS', $how_many

```

#### includes/modules/pages/gv_send/header_php.php
```
#15: 'NOTIFY_HEADER_START_GV_SEND'
#213: 'NOTIFY_HEADER_END_GV_SEND'

```

#### includes/modules/pages/specials/main_template_vars.php
```
#24: 'NOTIFY_SPECIALS_MAIN_TEMPLATE_VARS_SQL_STRING', array(), $specials_query_raw
#56: 'NOTIFY_SPECIALS_MAIN_TEMPLATE_VARS_END', array(), $list_box_contents

```

#### includes/modules/pages/specials/header_php.php
```
#10: 'NOTIFY_HEADER_START_SPECIALS'

```

#### includes/modules/pages/checkout_shipping/header_php.php
```
#11: 'NOTIFY_HEADER_START_CHECKOUT_SHIPPING'
#233: 'NOTIFY_HEADER_END_CHECKOUT_SHIPPING'

```

#### includes/modules/pages/page_not_found/header_php.php
```
#12: 'NOTIFY_HEADER_START_PAGE_NOT_FOUND'
#28: 'NOTIFY_HEADER_END_PAGE_NOT_FOUND'

```

#### includes/modules/pages/password_forgotten/header_php.php
```
#12: 'NOTIFY_HEADER_START_PASSWORD_FORGOTTEN'
#45: 'NOTIFY_PASSWORD_FORGOTTEN_VALIDATED', $email_address
#65: 'NOTIFY_PASSWORD_FORGOTTEN_CHANGED', $email_address, $check_customer->fields['customers_id'], $new_password
#68: 'NOTIFY_PASSWORD_FORGOTTEN_NOT_FOUND', $email_address
#80: 'NOTIFY_HEADER_END_PASSWORD_FORGOTTEN'

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
#11: 'NOTIFY_HEADER_START_POPUP_IMAGES_ADDITIONAL'
#47: 'NOTIFY_HEADER_END_POPUP_IMAGES_ADDITIONAL'

```

#### includes/modules/pages/document_product_info/main_template_vars.php
```
#15: 'NOTIFY_MAIN_TEMPLATE_VARS_START_DOCUMENT_PRODUCT_INFO'
#36: 'NOTIFY_PRODUCT_VIEWS_HIT_INCREMENTOR', (int)$_GET['products_id']
#134: 'NOTIFY_MAIN_TEMPLATE_VARS_PRODUCT_TYPE_VARS_DOCUMENT_PRODUCT_INFO'
#173: 'NOTIFY_MAIN_TEMPLATE_VARS_EXTRA_DOCUMENT_PRODUCT_INFO'
#181: 'NOTIFY_MAIN_TEMPLATE_VARS_END_DOCUMENT_PRODUCT_INFO'

```

#### includes/modules/pages/document_product_info/header_php.php
```
#12: 'NOTIFY_HEADER_START_DOCUMENT_PRODUCT_INFO'
#17: 'NOTIFY_HEADER_END_DOCUMENT_PRODUCT_INFO'

```

#### includes/modules/pages/document_product_info/main_template_vars_product_type.php
```
#18: 'NOTIFY_PRODUCT_TYPE_VARS_START_DOCUMENT_PRODUCT_INFO'
#36: 'NOTIFY_PRODUCT_TYPE_VARS_END_DOCUMENT_PRODUCT_INFO'

```

#### includes/modules/pages/gv_redeem/header_php.php
```
#10: 'NOTIFY_HEADER_START_GV_REDEEM'

```

#### includes/modules/pages/popup_image/header_php.php
```
#16: 'NOTIFY_HEADER_START_POPUP_IMAGES_ADDITIONAL'
#58: 'NOTIFY_HEADER_END_POPUP_IMAGES'

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
#15: 'NOTIFY_HEADER_START_DOWNLOAD'
#55: 'NOTIFY_DOWNLOAD_NO_MATCH_FOUND', $sql
#89: 'NOTIFY_CHECK_DOWNLOAD_HANDLER', $downloads, $downloads->fields, $origin_filename, $browser_filename, $source_directory, $file_exists, $service, $isExpired, $download_timestamp
#141: 'NOTIFY_DOWNLOAD_BROWSER_DETECTION', array(), $detectedBrowser, $_SERVER['HTTP_USER_AGENT'], $version, $browser_headers_override, $browser_extra_headers
#147: 'NOTIFY_DOWNLOAD_BEFORE_START', $_SESSION['customers_host_address'], $service, $origin_filename, $browser_filename, $source_directory, $downloadFilesize, $mime_type, $downloads->fields, $browser_headers
#148: 'NOTIFY_DOWNLOAD_READY_TO_START', $_SESSION['customers_host_address'], $service, $origin_filename, $browser_filename, $source_directory, $downloadFilesize, $mime_type, $downloads->fields, $browser_headers
#211: 'NOTIFY_DOWNLOAD_READY_TO_REDIRECT', array(), $service, $origin_filename, $browser_filename, $source_directory, $link_create_status
#215: 'NOTIFY_DOWNLOAD_READY_TO_STREAM', array(), $service, $origin_filename, $browser_filename, $source_directory, $downloadFilesize
#217: 'NOTIFY_HEADER_END_DOWNLOAD'

```

#### includes/modules/pages/checkout_payment_address/header_php.php
```
#12: 'NOTIFY_HEADER_START_CHECKOUT_PAYMENT_ADDRESS'
#45: 'NOTIFY_HEADER_END_CHECKOUT_PAYMENT_ADDRESS'

```

#### includes/modules/pages/product_reviews_write/header_php.php
```
#15: 'NOTIFY_HEADER_START_PRODUCT_REVIEWS_WRITE'
#51: 'NOTIFY_REVIEWS_WRITE_CAPTCHA_CHECK'
#65: 'NOTIFY_SPAM_DETECTED_DURING_WRITE_REVIEW'
#87: 'NOTIFY_REVIEW_INSERTED_DURING_WRITE_REVIEW'
#100: 'NOTIFY_SEND_ADMIN_EMAIL_WRITE_REVIEW'
#112: 'NOTIFY_EMAIL_READY_WRITE_REVIEW'
#140: 'NOTIFY_HEADER_END_PRODUCT_REVIEWS_WRITE'

```

#### includes/modules/pages/product_music_info/main_template_vars.php
```
#15: 'NOTIFY_MAIN_TEMPLATE_VARS_START_PRODUCT_MUSIC_INFO'
#36: 'NOTIFY_PRODUCT_VIEWS_HIT_INCREMENTOR', (int)$_GET['products_id']
#134: 'NOTIFY_MAIN_TEMPLATE_VARS_PRODUCT_TYPE_VARS_PRODUCT_MUSIC_INFO'
#177: 'NOTIFY_MAIN_TEMPLATE_VARS_EXTRA_PRODUCT_MUSIC_INFO'
#185: 'NOTIFY_MAIN_TEMPLATE_VARS_END_PRODUCT_MUSIC_INFO'

```

#### includes/modules/pages/product_music_info/main_template_vars_product_type.php
```
#18: 'NOTIFY_PRODUCT_TYPE_VARS_START_PRODUCT_MUSIC_INFO'
#71: 'NOTIFY_PRODUCT_TYPE_VARS_END_PRODUCT_MUSIC_INFO'

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
#12: 'NOTIFY_HEADER_START_ADVANCED_SEARCH_RESULTS'
#207: 'NOTIFY_SEARCH_COLUMNLIST_STRING'
#219: 'NOTIFY_SEARCH_SELECT_STRING'
#249: 'NOTIFY_SEARCH_FROM_STRING'
#407: 'NOTIFY_SEARCH_WHERE_STRING'
#469: 'NOTIFY_SEARCH_ORDERBY_STRING', $listing_sql
#481: 'NOTIFY_HEADER_END_ADVANCED_SEARCH_RESULTS', $keywords

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
#12: 'NOTIFY_HEADER_START_INDEX'
#65: 'NOTIFY_HEADER_END_INDEX'

```

#### includes/modules/pages/product_info/main_template_vars.php
```
#15: 'NOTIFY_MAIN_TEMPLATE_VARS_START_PRODUCT_INFO'
#36: 'NOTIFY_PRODUCT_VIEWS_HIT_INCREMENTOR', (int)$_GET['products_id']
#134: 'NOTIFY_MAIN_TEMPLATE_VARS_PRODUCT_TYPE_VARS_PRODUCT_INFO'
#173: 'NOTIFY_MAIN_TEMPLATE_VARS_EXTRA_PRODUCT_INFO'
#181: 'NOTIFY_MAIN_TEMPLATE_VARS_END_PRODUCT_INFO'

```

#### includes/modules/pages/product_info/header_php.php
```
#12: 'NOTIFY_HEADER_START_PRODUCT_INFO'
#38: 'NOTIFY_HEADER_END_PRODUCT_INFO'

```

#### includes/modules/pages/product_info/main_template_vars_product_type.php
```
#18: 'NOTIFY_PRODUCT_TYPE_VARS_START_PRODUCT_INFO'
#36: 'NOTIFY_PRODUCT_TYPE_VARS_END_PRODUCT_INFO'

```

#### includes/modules/pages/gv_faq/header_php.php
```
#12: 'NOTIFY_HEADER_START_GV_FAQ'
#33: 'NOTIFY_HEADER_END_GV_FAQ'

```

#### includes/modules/pages/account_notifications/header_php.php
```
#11: 'NOTIFY_HEADER_START_ACCOUNT_NOTIFICATION'
#135: 'NOTIFY_HEADER_END_ACCOUNT_NOTIFICATION'

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
#11: 'NOTIFY_HEADER_START_ACCOUNT'
#71: 'NOTIFY_HEADER_END_ACCOUNT'

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
#12: 'NOTIFY_HEADER_START_SHOPPING_CART'
#181: 'NOTIFY_HEADER_END_SHOPPING_CART'

```

#### includes/modules/pages/account_edit/header_php.php
```
#11: 'NOTIFY_HEADER_START_ACCOUNT_EDIT'
#94: 'NOTIFY_NICK_CHECK_FOR_EXISTING_EMAIL', $email_address, $nick_error, $nick
#103: 'NOTIFY_HEADER_ACCOUNT_EDIT_VERIFY_COMPLETE'
#107: 'NOTIFY_NICK_UPDATE_EMAIL_ADDRESS', $nick, $db->prepareInput($email_address)
#152: 'NOTIFY_HEADER_ACCOUNT_EDIT_UPDATES_COMPLETE'
#211: 'NOTIFY_HEADER_END_ACCOUNT_EDIT'

```

#### includes/modules/pages/site_map/header_php.php
```
#12: 'NOTIFY_HEADER_START_SITE_MAP'
#26: 'NOTIFY_HEADER_END_SITE_MAP'

```

#### includes/modules/pages/login/header_php.php
```
#12: 'NOTIFY_HEADER_START_LOGIN'
#57: 'NOTIFY_LOGIN_BANNED'
#70: 'NOTIFY_PROCESS_3RD_PARTY_LOGINS', $email_address, $password, $loginAuthorized
#115: 'NOTIFY_LOGIN_SUCCESS'
#160: 'NOTIFY_LOGIN_FAILURE'
#172: 'NOTIFY_HEADER_END_LOGIN'

```

#### includes/modules/pages/checkout_process/header_php.php
```
#11: 'NOTIFY_HEADER_START_CHECKOUT_PROCESS'
#18: 'NOTIFY_CHECKOUT_PROCESS_BEFORE_CART_RESET', $insert_id
#30: 'NOTIFY_HEADER_END_CHECKOUT_PROCESS'

```

#### includes/modules/pages/address_book_process/header_php.php
```
#11: 'NOTIFY_HEADER_START_ADDRESS_BOOK_PROCESS'
#33: 'NOTIFY_HEADER_ADDRESS_BOOK_DELETION_DONE'
#170: 'NOTIFY_ADDRESS_BOOK_PROCESS_VALIDATION', array(), $error
#199: 'NOTIFY_MODULE_ADDRESS_BOOK_UPDATED_ADDRESS_BOOK_RECORD', array_merge(array('address_book_id' => $_GET['edit'], 'customers_id' => $_SESSION['customer_id']), $sql_data_array)
#217: 'NOTIFY_MODULE_ADDRESS_BOOK_UPDATED_CUSTOMER_RECORD', array_merge(array('customers_id' => $_SESSION['customer_id']), $sql_data_array)
#225: 'NOTIFY_MODULE_ADDRESS_BOOK_ADDED_ADDRESS_BOOK_RECORD', array_merge(array('address_id' => $new_address_book_id), $sql_data_array)
#247: 'NOTIFY_MODULE_ADDRESS_BOOK_UPDATED_PRIMARY_CUSTOMER_RECORD', array_merge(array('address_id' => $new_address_book_id, 'customers_id' => $_SESSION['customer_id']), $sql_data_array)
#342: 'NOTIFY_HEADER_END_ADDRESS_BOOK_PROCESS'

```

#### admin/attributes_controller.php
```
#421: 'NOTIFY_ATTRIBUTE_CONTROLLER_ADD_PRODUCT_ATTRIBUTES', $products_attributes_id
#565: 'NOTIFY_ATTRIBUTE_CONTROLLER_UPDATE_PRODUCT_ATTRIBUTE', $attribute_id
#584: 'NOTIFY_ATTRIBUTE_CONTROLLER_DELETE_ATTRIBUTE', array('attribute_id' => $attribute_id), $attribute_id
#601: 'NOTIFY_ATTRIBUTE_CONTROLLER_DELETE_ALL', array('pID' => $_POST['products_filter'])
#615: 'NOTIFY_ATTRIBUTE_CONTROLLER_DELETE_OPTION_NAME_VALUES', array('pID' => $_POST['products_filter'], 'options_id' => $_POST['products_options_id_all'])

```

#### admin/product.php
```
#15: 'NOTIFY_BEGIN_ADMIN_PRODUCTS', $action

```

#### admin/languages.php
```
#179: 'NOTIFY_ADMIN_LANGUAGE_INSERT', (int)$insert_id
#255: 'NOTIFY_ADMIN_LANGUAGE_DELETE', (int)$lID

```

#### admin/category_product_listing.php
```
#847: 'NOTIFY_ADMIN_PROD_LISTING_ADD_ICON', $product, $additional_icons

```

#### admin/admin_activity.php
```
#293: 'NOTIFY_ADMIN_ACTIVITY_LOG_RESET'

```

#### admin/includes/classes/class.admin.zcObserverLogEventListener.php
```
#58: $this->notifier->notify('NOTIFY_ADMIN_FIRE_LOG_WRITERS', $log_data
#193: $this->notifier->notify('NOTIFY_ADMIN_FIRE_LOG_WRITER_RESET'
#209: 'NOTIFY_ADMIN_ACTIVITY_LOG_EVENT', $message, $severity

```

#### admin/includes/init_includes/init_languages.php
```
#19: 'NOTIFY_LANGUAGE_CHANGE_REQUESTED_BY_ADMIN_VISITOR', $_GET['language'], $lng

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
#27: 'NOTIFY_ADMIN_FOOTER_END'

```

#### admin/includes/functions/html_output.php
```
#49: 'NOTIFY_SEFU_INTERCEPT_ADMCATHREF', array(), $link, $page, $parameters, $connection

```

#### admin/includes/functions/functions_prices.php
```
#120: 'ZEN_GET_PRODUCTS_BASE_PRICE', $products_id, $products_base_price, $base_price_is_handled

```

#### admin/includes/functions/localization.php
```
#42: 'ADMIN_CURRENCY_EXCHANGE_RATE_MULTIPLIER', $currency->fields['code'], $multiplier, $rate
#53: 'ADMIN_CURRENCY_EXCHANGE_RATE_SINGLE', $currency->fields['code'], $rate
#75: 'ADMIN_CURRENCY_EXCHANGE_RATES_UPDATED', $msg

```

#### admin/includes/functions/general.php
```
#1200: 'NOTIFIER_ADMIN_ZEN_REMOVE_CATEGORY', array(), $category_id
#1361: 'NOTIFIER_ADMIN_ZEN_REMOVE_PRODUCT', array(), $product_id, $ptc
#1448: 'NOTIFIER_ADMIN_ZEN_PRODUCTS_ATTRIBUTES_DOWNLOAD_DELETE', array(), $product_id
#1460: 'NOTIFIER_ADMIN_ZEN_REMOVE_ORDER', array(), $order_id, $restock
#2098: 'FUNCTIONS_LOOKUPS_OPTION_NAME_NO_VALUES_OPT_TYPE', $opt_type, $test_var
#2359: 'NOTIFIER_ADMIN_ZEN_DELETE_PRODUCTS_ATTRIBUTES', array(), $delete_product_id
#3325: 'NOTIFY_TEST_DOWNLOADABLE_FILE_EXISTS', $check_filename, $handler

```

#### admin/includes/modules/new_product_preview.php
```
#24: 'NOTIFY_ADMIN_PRODUCT_IMAGE_UPLOADED', $products_image, $products_image_name

```

#### admin/includes/modules/copy_product.php
```
#43: 'NOTIFY_ADMIN_PRODUCT_COPY_TO_ATTRIBUTES', $pInfo, $contents

```

#### admin/options_values_manager.php
```
#169: 'OPTIONS_VALUES_MANAGER_DELETE_VALUE', array('value_id' => $value_id)
#483: 'OPTIONS_VALUES_MANAGER_DELETE_VALUES_OF_OPTIONNAME', array('current_products_id' => $current_products_id, 'remove_ids' => $remove_downloads_ids, 'options_id' => $options_id_from, 'options_values_id' => $options_values_values_id_from)

```

#### admin/coupon_admin.php
```
#101: 'ADMIN_COUPON_CODE_EMAILED_TO_CUSTOMER', $coupon_result->fields['coupon-code'], $mail->fields['customers_email_address']

```

#### admin/categories.php
```
#39: 'NOTIFY_BEGIN_ADMIN_CATEGORIES', $action

```

#### admin/customers.php
```
#35: 'NOTIFY_ADMIN_CUSTOMERS_LIST_ADDRESSES', $addresses_query
#239: 'NOTIFY_ADMIN_CUSTOMERS_UPDATE_VALIDATE', array(), $error
#297: 'NOTIFY_ADMIN_CUSTOMERS_B4_ADDRESS_UPDATE', array('customers_id' => $customers_id, 'address_book_id' => $default_address_id), $sql_data_array
#301: 'ADMIN_CUSTOMER_UPDATE', (int)$customers_id, $default_address_id, $sql_data_array
#372: 'NOTIFIER_ADMIN_ZEN_CUSTOMERS_DELETE_CONFIRM', array('customers_id' => $customers_id)
#737: 'NOTIFY_ADMIN_CUSTOMERS_CUSTOMER_EDIT', $cInfo, $additional_fields
#1133: 'NOTIFY_ADMIN_CUSTOMERS_LISTING_HEADER', array(), $additional_headings
#1198: 'NOTIFY_ADMIN_CUSTOMERS_LISTING_NEW_FIELDS', array(), $new_fields, $disp_order
#1308: 'NOTIFY_ADMIN_CUSTOMERS_LISTING_ELEMENT', $customer, $additional_columns
#1398: 'NOTIFY_ADMIN_CUSTOMERS_MENU_BUTTONS', $cInfo, $contents
#1424: 'NOTIFY_ADMIN_CUSTOMERS_MENU_BUTTONS_END', (isset($cInfo) ? $cInfo : new stdClass), $contents

```

#### admin/orders.php
```
#78: 'NOTIFY_ADMIN_ORDER_PREDISPLAY_HOOK', $oID, $action
#304: 'NOTIFY_ADMIN_ORDERS_DEFAULT_ACTION', $oID, $order
#414: 'NOTIFY_ADMIN_ORDERS_EDIT_BEGIN', $oID, $order
#572: <?php 'NOTIFY_ADMIN_ORDERS_PAYMENTDATA_COLUMN2', $oID, $order ?>
#770: 'NOTIFY_ADMIN_ORDERS_EDIT_BUTTONS', $oID, $order, $extra_buttons
#797: 'NOTIFY_ADMIN_ORDERS_MENU_LEGEND', array(), $extra_legends
#855: 'NOTIFY_ADMIN_ORDERS_LIST_EXTRA_COLUMN_HEADING', array(), $extra_headings
#960: 'NOTIFY_ADMIN_ORDERS_SHOW_ORDER_DIFFERENCE', array(), $orders->fields, $show_difference, $extra_action_icons
#986: 'NOTIFY_ADMIN_ORDERS_LIST_EXTRA_COLUMN_DATA', (isset($oInfo) ? $oInfo : array()), $orders->fields, $extra_data
#1057: 'NOTIFY_ADMIN_ORDERS_MENU_BUTTONS', $oInfo, $contents
#1113: 'NOTIFY_ADMIN_ORDERS_MENU_BUTTONS_END', (isset($oInfo) ? $oInfo : array()), $contents

```

#### admin/options_name_manager.php
```
#222: 'OPTIONS_NAME_MANAGER_DELETE_OPTION', array('option_id' => $option_id, 'options_values_id' => (int)$remove_option_value['products_options_values_id'])
#331: 'OPTIONS_NAME_MANAGER_UPDATE_OPTIONS_VALUES_DELETE', array( 'products_id' => $all_update_product['products_id'], 'options_id' => $all_options_value['products_options_id'], 'options_values_id' => $all_options_value['products_options_values_id']) 

```

#### notifier_report.php
```
#46: // Determine if the current line contains a '->notify', continuing if not. // $next_pos = strpos($lines[$i], '->notify'
#71: '', '', '', '$GLOBALS[\'zco_notifier\']->notify(', '',
