---
title: How can I limit the age of my customers to people over 18?
description: Selling age-restricted products 
category: miscellaneous
weight: 10
---

There is no certain way to check on a visitor's age, but you can check that the date of birth that they have given you would make them at least 18 (or any other age you choose).

To do this create an override file in your template for <code>includes/modules/create_account.php</code>.

Find the section of code that reads
<pre>
  if (ACCOUNT_DOB == 'true') {
    // ... additional checks here 
    if (ENTRY_DOB_MIN_LENGTH > 0 or !empty($_POST['dob'])) {
      if (substr_count($dob,'/') > 2 || checkdate((int)substr(zen_date_raw($dob), 4, 2), (int)substr(zen_date_raw($dob), 6, 2), (int)substr(zen_date_raw($dob), 0, 4)) == false) {
        $error = true;
        $messageStack->add('create_account', ENTRY_DATE_OF_BIRTH_ERROR);
      }
    }
  }
</pre>

and expand it to (setting the minimum age to whatever you wish)

<pre>
  if (ACCOUNT_DOB == 'true') {
    // ... additional checks here 
    if (ENTRY_DOB_MIN_LENGTH > 0 or !empty($_POST['dob'])) {
      if (substr_count($dob,'/') > 2 || checkdate((int)substr(zen_date_raw($dob), 4, 2), (int)substr(zen_date_raw($dob), 6, 2), (int)substr(zen_date_raw($dob), 0, 4)) == false) {
        $error = true;
        $messageStack->add('create_account', ENTRY_DATE_OF_BIRTH_ERROR);
      }
      $minimum_age = 18;
      $acceptable_dob = (date('Y') - $minimum_age) . date('md');
      if (zen_date_raw($dob) > $acceptable_dob) {
        $error = true;
        $messageStack->add('create_account', ENTRY_DATE_OF_BIRTH_UNDERAGE);
      }               
    }
  }
</pre>


Then create an override file for your <code>includes/languages/english/create_account.php</code> file and place the following line in there, changing the text to suit your style of feeding errors back to visitors

<pre>
define('ENTRY_DATE_OF_BIRTH_UNDERAGE','Sorry, but you must be at least 18 to register to use this site');
</pre>
