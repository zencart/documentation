---
title: Configuration ≫ Customer Details
category: admin_pages
weight: 50 
---

<h2 id="email_salutation">Email Salutation</h2>

<div class='indent'>Key: <b>ACCOUNT_GENDER</b><br />
Path: <b>Configuration > Customer Details</b><br />
Description: Display salutation choice during account creation and with account information</div>


<h2 id="date_of_birth">Date of Birth</h2>

<div class='indent'>Key: <b>ACCOUNT_DOB</b><br />
Path: <b>Configuration > Customer Details</b><br />
Description: Display date of birth field during account creation and with account information<br />NOTE: Set Minimum Value Date of Birth to blank for not required<br />Set Minimum Value Date of Birth > 0 to require</div>


<h2 id="company">Company</h2>

<div class='indent'>Key: <b>ACCOUNT_COMPANY</b><br />
Path: <b>Configuration > Customer Details</b><br />
Description: Display company field during account creation and with account information</div>


<h2 id="address_line_2">Address Line 2</h2>

<div class='indent'>Key: <b>ACCOUNT_SUBURB</b><br />
Path: <b>Configuration > Customer Details</b><br />
Description: Display address line 2 field during account creation and with account information</div>


<h2 id="state">State</h2>

<div class='indent'>Key: <b>ACCOUNT_STATE</b><br />
Path: <b>Configuration > Customer Details</b><br />
Description: Display state field during account creation and with account information</div>


<h2 id="state_field__display_as_pulldown_when_possible">State field - Display as pulldown when possible?</h2>

<div class='indent'>Key: <b>ACCOUNT_STATE_DRAW_INITIAL_DROPDOWN</b><br />
Path: <b>Configuration > Customer Details</b><br />
Description: If zones have been defined for a country, the State field may be displayed as a dropdown populated by the defined zones. Otherwise a text field is displayed for customer entry.<br><strong>true</strong>: When a State field is used, display a pulldown menu whenever possible.<br><strong>false</strong>: When a State field is used, always display a text input field.</div>


<h2 id="create_account_default_country">Create Account Default Country</h2>

<div class='indent'>Key: <b>SHOW_CREATE_ACCOUNT_DEFAULT_COUNTRY</b><br />
Path: <b>Configuration > Customer Details</b><br />
Description: Set the default/pre-selected country on the Create Account page to:<br>(default is United States)</div>


<h2 id="fax_number">Fax Number</h2>

<div class='indent'>Key: <b>ACCOUNT_FAX_NUMBER</b><br />
Path: <b>Configuration > Customer Details</b><br />
Description: Display fax number field during account creation and with account information</div>


<h2 id="show_newsletter_checkbox">Show Newsletter Checkbox</h2>

<div class='indent'>Key: <b>ACCOUNT_NEWSLETTER_STATUS</b><br />
Path: <b>Configuration > Customer Details</b><br />
Description: Show Newsletter Checkbox<br />0= off<br />1= Display Unchecked<br />2= Display Checked<br /><strong>Note: Defaulting this to accepted may be in violation of certain regulations for your state or country</strong></div>


<h2 id="customer_default_email_preference">Customer Default Email Preference</h2>

<div class='indent'>Key: <b>ACCOUNT_EMAIL_PREFERENCE</b><br />
Path: <b>Configuration > Customer Details</b><br />
Description: Set the Default Customer Default Email Preference<br />0= Text<br />1= HTML<br /></div>


<h2 id="customer_product_notification_status">Customer Product Notification Status</h2>

<div class='indent'>Key: <b>CUSTOMERS_PRODUCTS_NOTIFICATION_STATUS</b><br />
Path: <b>Configuration > Customer Details</b><br />
Description: Customer should be asked about product notifications after checkout success and in account preferences<br />0= Never ask<br />1= Ask (ignored on checkout if has already selected global notifications)<br /><br />Note: Sidebox must be turned off separately</div>


<h2 id="customer_shop_status__view_shop_and_prices">Customer Shop Status - View Shop and Prices</h2>

<div class='indent'>Key: <b>CUSTOMERS_APPROVAL</b><br />
Path: <b>Configuration > Customer Details</b><br />
Description: Customer must be approved to shop<br />0= Not required<br />1= Must login to browse<br />2= May browse but no prices unless logged in<br />3= Showroom Only<br /><br />It is recommended that Option 2 be used for the purposes of Spiders if you wish customers to login to see prices.</div>


<h2 id="customer_approval_status__authorization_pending">Customer Approval Status - Authorization Pending</h2>

<div class='indent'>Key: <b>CUSTOMERS_APPROVAL_AUTHORIZATION</b><br />
Path: <b>Configuration > Customer Details</b><br />
Description: Customer must be Authorized to shop<br />0= Not required<br />1= Must be Authorized to Browse<br />2= May browse but no prices unless Authorized<br />3= Customer May Browse and May see Prices but Must be Authorized to Buy<br /><br />It is recommended that Option 2 or 3 be used for the purposes of Spiders</div>


<h2 id="customer_authorization_filename">Customer Authorization: filename</h2>

<div class='indent'>Key: <b>CUSTOMERS_AUTHORIZATION_FILENAME</b><br />
Path: <b>Configuration > Customer Details</b><br />
Description: Customer Authorization filename<br />Note: Do not include the extension<br />Default=customers_authorization</div>


<h2 id="customer_authorization_hide_header">Customer Authorization: Hide Header</h2>

<div class='indent'>Key: <b>CUSTOMERS_AUTHORIZATION_HEADER_OFF</b><br />
Path: <b>Configuration > Customer Details</b><br />
Description: Customer Authorization: Hide Header <br />(true=hide false=show)</div>


<h2 id="customer_authorization_hide_column_left">Customer Authorization: Hide Column Left</h2>

<div class='indent'>Key: <b>CUSTOMERS_AUTHORIZATION_COLUMN_LEFT_OFF</b><br />
Path: <b>Configuration > Customer Details</b><br />
Description: Customer Authorization: Hide Column Left <br />(true=hide false=show)</div>


<h2 id="customer_authorization_hide_column_right">Customer Authorization: Hide Column Right</h2>

<div class='indent'>Key: <b>CUSTOMERS_AUTHORIZATION_COLUMN_RIGHT_OFF</b><br />
Path: <b>Configuration > Customer Details</b><br />
Description: Customer Authorization: Hide Column Right <br />(true=hide false=show)</div>


<h2 id="customer_authorization_hide_footer">Customer Authorization: Hide Footer</h2>

<div class='indent'>Key: <b>CUSTOMERS_AUTHORIZATION_FOOTER_OFF</b><br />
Path: <b>Configuration > Customer Details</b><br />
Description: Customer Authorization: Hide Footer <br />(true=hide false=show)</div>


<h2 id="customers_referral_status">Customers Referral Status</h2>

<div class='indent'>Key: <b>CUSTOMERS_REFERRAL_STATUS</b><br />
Path: <b>Configuration > Customer Details</b><br />
Description: Customers Referral Code is created from<br />0= Off<br />1= 1st Discount Coupon Code used<br />2= Customer can add during create account or edit if blank<br /><br />NOTE: Once the Customers Referral Code has been set it can only be changed by the Administrator</div>


