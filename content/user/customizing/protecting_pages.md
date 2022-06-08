---
title: Protecting pages 
description: Ensuring pages are only accessible by certain users 
category: customizing 
weight: 10
---

## Restricting page to logged in users

As an example, we'll use the [built-in extra page](/user/template/extra_pages/)  page_2 (`index.php?main_page=page_2`). 

Modify `includes/modules/pages/page_2/header_php.php` to include at the top: 

```
// if the customer is not logged on, redirect them to the login page
  if (!zen_is_logged_in() || zen_in_guest_checkout()) {
    global $messageStack; 
    $messageStack->add_session('login','Restricted content for approved accountholders only - please login', 'warning'); 
    $_SESSION['navigation']->set_snapshot();
    zen_redirect(zen_href_link(FILENAME_LOGIN, '', 'SSL'));
  } 
```

## Restricting page to a Customer Group 

Note: This takes advange of the 1.5.8 feature [Customer Groups](/user/admin_pages/customers/customer_groups/), so is only available in Zen Cart 1.5.8 and above.

Use the logic above to give the right message to non-logged-in users, then add this block next.  We are assuming group "1" is Wholesalers, and we'll restrict page_2 to this group. 


```
// if the customer is not in group 1, redirect to page not found
  $allowed_group = 1; 
  if (!zen_customer_belongs_to_group((int)$_SESSION['customer_id'], $allowed_group, true)) {
    global $messageStack; 
    $messageStack->add_session('header','Restricted content for wholesale accounts only', 'warning'); 
    zen_redirect(zen_href_link(FILENAME_PAGE_NOT_FOUND, '', 'SSL'));
  } 
```
