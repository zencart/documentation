---
title: Configuration-My Store
description: Zen Cart Configuration-My Store Admin Page 
category: admin_pages
weight: 10
---

<b>Store Name</b>

<div class='indent'>The name of my store</div>


<b>Store Owner</b>

<div class='indent'>The name of my store owner</div>


<b>Telephone - Customer Service</b>

<div class='indent'>Enter a telephone number for customers to reach your Customer Service department. This number may be sent as part of payment transaction details.</div>


<b>Country</b>

<div class='indent'>The country my store is located in <br /><br /><strong>Note: Please remember to update the store zone.</strong></div>


<b>Zone</b>

<div class='indent'>The zone my store is located in</div>


<b>Store Address and Phone</b>

<div class='indent'>This is the Store Name, Address and Phone used on printable documents and displayed online</div>


<b>Expected Sort Order</b>

<div class='indent'>This is the sort order used in the expected products box.</div>


<b>Expected Sort Field</b>

<div class='indent'>The column to sort by in the expected products box.</div>


<b>Switch To Default Language Currency</b>

<div class='indent'>Automatically switch to the language's currency when it is changed</div>


<b>Language Selector</b>

<div class='indent'>Should the default language be based on the Store preferences, or the customer's browser settings?<br /><br />Default: Store's default settings</div>


<b>Display Cart After Adding Product</b>

<div class='indent'>Display the shopping cart after adding a product (or return back to their origin)</div>


<b>Default Search Operator</b>

<div class='indent'>Default search operators</div>


<b>Include meta-tags in product search?</b>

<div class='indent'>Should a product's meta-tag keywords and meta-tag descriptions be considered in any <code>advanced_search_results</code> displayed?</div>


<b>Show Category Counts</b>

<div class='indent'>Count recursively how many products are in each category</div>


<b>Show Category Counts - Admin</b>

<div class='indent'>Show Category Counts in Admin?</div>


<b>Show linked status for categories</b>

<div class='indent'>Show Category products linked status?</div>


<b>Tax Decimal Places</b>

<div class='indent'>Pad the tax value this amount of decimal places</div>


<b>Display Prices with Tax</b>

<div class='indent'>Display prices with tax included (true) or add the tax at the end (false)</div>


<b>Display Prices with Tax in Admin</b>

<div class='indent'>Display prices with tax included (true) or add the tax at the end (false) in Admin(Invoices)</div>


<b>Basis of Product Tax</b>

<div class='indent'>On what basis is Product Tax calculated. Options are<br />Shipping - Based on customers Shipping Address<br />Billing Based on customers Billing address<br />Store - Based on Store address if Billing/Shipping Zone equals Store zone</div>


<b>Basis of Shipping Tax</b>

<div class='indent'>On what basis is Shipping Tax calculated. Options are<br />Shipping - Based on customers Shipping Address<br />Billing Based on customers Billing address<br />Store - Based on Store address if Billing/Shipping Zone equals Store zone - Can be overriden by correctly written Shipping Module</div>


<b>Sales Tax Display Status</b>

<div class='indent'>Always show Sales Tax even when amount is $0.00?<br />0= Off<br />1= On</div>


<b>Show Split Tax Lines</b>

<div class='indent'>If multiple tax rates apply, show each rate as a separate line at checkout</div>


<b>Store Status</b>

<div class='indent'>What is your Store Status<br />0= Normal Store<br />1= Showcase no prices<br />2= Showcase with prices</div>


<b>PA-DSS Admin Session Timeout Enforced?</b>

<div class='indent'>PA-DSS Compliance requires that any Admin login sessions expire after 15 minutes of inactivity. <strong>Disabling this makes your site NON-COMPLIANT with PA-DSS rules, thus invalidating any certification.</strong></div>


<b>PA-DSS Strong Password Rules Enforced?</b>

<div class='indent'>PA-DSS Compliance requires that admin passwords must be changed after 90 days and cannot re-use the last 4 passwords. <strong>Disabling this makes your site NON-COMPLIANT with PA-DSS rules, thus invalidating any certification.</strong></div>


<b>PA-DSS Ajax Checkout?</b>

<div class='indent'>PA-DSS Compliance requires that for some inbuilt payment methods, that we use ajax to draw the checkout confirmation screen. While this will only happen if one of those payment methods is actually present, some people may want the traditional checkout flow <strong>Disabling this makes your site NON-COMPLIANT with PA-DSS rules, thus invalidating any certification.</strong></div>


<b>Admin Session Time Out in Seconds</b>

<div class='indent'>Enter the time in seconds.<br />Max allowed is 900 for PCI Compliance Reasons.<br /> Default=900<br />Example: 900= 15 min <br /><br />Note: Too few seconds can result in timeout issues when adding/editing products</div>


<b>Admin Set max_execution_time for processes</b>

<div class='indent'>Enter the time in seconds for how long the max_execution_time of processes should be. Default=60<br />Example: 60= 1 minute<br /><br />Note: Changing the time limit is only needed if you are having problems with the execution time of a process</div>


<b>Show if version update available</b>

<div class='indent'>Automatically check to see if a new version of Zen Cart is available. Enabling this can sometimes slow down the loading of Admin pages. (Displayed on main Index page after login, and Server Info page.)</div>


<b>Server Uptime</b>

<div class='indent'>Displaying Server uptime can cause entries in error logs on some servers. (true = Display, false = don't display)</div>


<b>Missing Page Check</b>

<div class='indent'>Zen Cart can check for missing pages in the URL and redirect to Index page. For debugging you may want to turn this off. <br /><br /><strong>Default=On</strong><br />On = Send missing pages to 'index'<br />Off = Don't check for missing pages<br />Page Not Found = display the Page-Not-Found page</div>


<b>Currency Conversion Ratio</b>

<div class='indent'>When auto-updating currencies, what "uplift" ratio should be used to calculate the exchange rate used by your store?<br />ie: the bank rate is obtained from the currency-exchange servers; how much extra do you want to charge in order to make up the difference between the bank rate and the consumer rate?<br /><br /><strong>Default: 1.05 </strong><br />This will cause the published bank rate to be multiplied by 1.05 to set the currency rates in your store.</div>


<b>Currency Exchange Rate: Primary Source</b>

<div class='indent'>Where to request external currency updates from (Primary source)<br><br>Additional sources can be installed via plugins.</div>


<b>Currency Exchange Rate: Secondary Source</b>

<div class='indent'>Where to request external currency updates from (Secondary source)<br><br>Additional sources can be installed via plugins.</div>


<b>HTML Editor</b>

<div class='indent'>Please select the HTML/Rich-Text editor you wish to use for composing Admin-related emails, newsletters, and product descriptions</div>


<b>Default for Notify Customer on Order Status Update?</b>

<div class='indent'>Set the default email behavior on status update to Send Email, Do Not Send Email, or Hide Update.</div>


<b>Customer Place Order: Single Admin ID</b>

<div class='indent'>Identify the ID of an admin that is permitted to use the <em>Place Order</em> feature on the customers' listing, regardless of their assigned admin-profile. Set the value to 0 to disable the <em>Single Admin ID</em> feature.<br /><br /><b>Default: 1</b><br /></div>


<b>Customer Place Order: Admin Profiles</b>

<div class='indent'>Identify the admin <em>User Profile IDs</em> that are permitted to use the <em>Place Order</em> feature on the customers' listing &mdash; all admins that are in these profiles are permitted. Enter the value as a comma-separated list (intervening blanks are OK) of Admin Profile IDs, e.g. <b>1, 2, 3</b>. Set the value to 0 to disable the <em>Admin Profiles</em> feature.<br /><br /><b>Default: 1 (All Superusers)</b><br /></div>


<b>Customer Place Order: Passwordless Login</b>

<div class='indent'>Login directly to store without entering credentials</div>


