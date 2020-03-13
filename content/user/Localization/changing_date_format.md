---
title: Date format - changing it from the US format to dd/mm/yyyy
category: localization
weight: 1
---

There are a number of different date formats used around the world, and the approach for changing to any of them is broadly the same. In this tutorial we'll show how to change from the default US format to the dd/mm/yyyy format used in most other English-speaking countries and those speaking many other languages. As date formats are generally language-specific (or in the case of English, dialect-specific) we'll be editing two Zen Cart language files to make this change.  

### 1\. open file includes/languages/YOURTEMPLATE/YOURLANGUAGE.php

(if this file doesn't exist, create it by copying the file `includes/languages/YOURLANGUAGE.php` to this location).  

### 2\. find this section:

<pre>
@setlocale(LC_TIME, 'en_US.ISO_8859-1');

define('DATE_FORMAT_SHORT', '%m/%d/%Y'); // this is used for strftime()

define('DATE_FORMAT_LONG', '%A %d %B, %Y'); // this is used for strftime()

define('DATE_FORMAT', 'm/d/Y'); // this is used for date()

define('DATE_TIME_FORMAT', DATE_FORMAT_SHORT . ' %H:%M:%S');
</pre>

and replace with:  

<pre>
@setlocale(LC_TIME, 'en_GB.ISO_8859-1');

define('DATE_FORMAT_SHORT', '%d/%m/%Y'); // this is used for strftime()

define('DATE_FORMAT_LONG', '%A %d %B, %Y'); // this is used for strftime()

define('DATE_FORMAT', 'd/m/Y'); // this is used for date()

define('DATE_TIME_FORMAT', DATE_FORMAT_SHORT . ' %H:%M:%S');
</pre>

### 3\. in the same file find this section:

<pre>
// Return date in raw format

// $date should be in format mm/dd/yyyy

// raw date is in format YYYYMMDD, or DDMMYYYY

if (!function_exists('zen_date_raw')) {

  function zen_date_raw($date, $reverse = false) {

    if ($reverse) {

      return substr($date, 3, 2) . substr($date, 0, 2) . substr($date, 6, 4);

    } else {

      return substr($date, 6, 4) . substr($date, 0, 2) . substr($date, 3, 2);

    }

  }

}
</pre>

and replace with:  

<pre>
// Return date in raw format

// $date should be in format dd/mm/yyyy

// raw date is in format YYYYMMDD, or DDMMYYYY

if (!function_exists('zen_date_raw')) {

  function zen_date_raw($date, $reverse = false) {

    if ($reverse) {

      return substr($date, 0, 2) . substr($date, 3, 2) . substr($date, 6, 4);

    } else {

      return substr($date, 6, 4) . substr($date, 3, 2) . substr($date, 0, 2);

    }

  }

}  
</pre>


### 4\. In the same file find this section:

<pre>
// text for date of birth example

define('DOB_FORMAT_STRING', 'mm/dd/yyyy');

</pre>

and replace with:  

<pre>
// text for date of birth example

define('DOB_FORMAT_STRING', 'dd/mm/yyyy');

</pre>

### 5\. In the same file find this section:

`define('ENTRY_DATE_OF_BIRTH_ERROR', 'Is your birth date correct? Our system requires the date in this format: MM/DD/YYYY (eg 05/21/1970)');`

`define('ENTRY_DATE_OF_BIRTH_TEXT', '* (eg. 05/21/1970)'); `

and replace with:  


`define('ENTRY_DATE_OF_BIRTH_ERROR', 'Is your birth date correct? Our system requires the date in this format: DD/MM/YYYY (eg 21/05/1970)');`

`define('ENTRY_DATE_OF_BIRTH_TEXT', '* (eg. 21/05/1970)');`


### 6\. Open file admin/includes/languages/YOURLANGUAGE.php

(this file cannot be over-ridden at present, so you will need to edit the file directly and be careful to reapply the changes if you upgrade to a later version of Zen Cart)  

### 7\. Find this section:

<pre>
setlocale(LC_TIME, 'en_US.ISO_8859-1');

define('DATE_FORMAT_SHORT', '%m/%d/%Y'); // this is used for strftime()

define('DATE_FORMAT_LONG', '%A %d %B, %Y'); // this is used for strftime()

define('DATE_FORMAT', 'm/d/Y'); // this is used for date()

define('PHP_DATE_TIME_FORMAT', 'm/d/Y H:i:s'); // this is used for date()

define('DATE_TIME_FORMAT', DATE_FORMAT_SHORT . ' %H:%M:%S');

define('DATE_FORMAT_SPIFFYCAL', 'MM/dd/yyyy'); //Use only 'dd', 'MM' and 'yyyy' here in any order
</pre>

and replace with:  

<pre>
setlocale(LC_TIME, 'en_GB.ISO_8859-1');

define('DATE_FORMAT_SHORT', '%d/%m/%Y'); // this is used for strftime()

define('DATE_FORMAT_LONG', '%A %d %B, %Y'); // this is used for strftime()

define('DATE_FORMAT', 'd/m/Y'); // this is used for date()

define('PHP_DATE_TIME_FORMAT', 'd/m/Y H:i:s'); // this is used for date()

define('DATE_TIME_FORMAT', DATE_FORMAT_SHORT . ' %H:%M:%S');

define('DATE_FORMAT_SPIFFYCAL', 'dd/MM/yyyy'); //Use only 'dd', 'MM' and 'yyyy' here in any order
</pre>

### 8\. In the same file find this section:

<pre>
// Return date in raw format

// $date should be in format mm/dd/yyyy

// raw date is in format YYYYMMDD, or DDMMYYYY

function zen_date_raw($date, $reverse = false) {

  if ($reverse) {

    return substr($date, 3, 2) . substr($date, 0, 2) . substr($date, 6, 4);

  } else {

    return substr($date, 6, 4) . substr($date, 0, 2) . substr($date, 3, 2);

  }

}
</pre>
and replace with:

<pre>
// Return date in raw format

// $date should be in format dd/mm/yyyy

// raw date is in format YYYYMMDD, or DDMMYYYY

function zen_date_raw($date, $reverse = false) {

  if ($reverse) {

    return substr($date, 0, 2) . substr($date, 3, 2) . substr($date, 6, 4);

  } else {

    return substr($date, 6, 4) . substr($date, 3, 2) . substr($date, 0, 2);

  }

}
</pre>
### 9\. In the same file find this section:

<pre>
// text for date of birth example

define('DOB_FORMAT_STRING', 'mm/dd/yyyy');

and replace with:  

// text for date of birth example

define('DOB_FORMAT_STRING', 'dd/mm/yyyy');
</pre>

### 10\. In the same file find this section:

`define('JS_DOB', '* The \'Date of Birth\' entry must be in the format: xx/xx/xxxx (month/date/year).\n');`

and replace with:  

`define('JS_DOB', '* The \'Date of Birth\' entry must be in the format: xx/xx/xxxx (date/month/year).\n');`

### 11\. In the same file find this section:

`define('ENTRY_DATE_OF_BIRTH_ERROR', '&nbsp;<span class="errorText">(eg. 05/21/1970)</span>');`

and replace with:  

`define('ENTRY_DATE_OF_BIRTH_ERROR', '&nbsp;<span class="errorText">(eg. 21/05/1970)</span>');`

And that's it, you're done!  

