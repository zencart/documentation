---
title: Date format - changing it from the US format to dd/mm/yyyy
description: Localizing data display 
category: localization
weight: 10
---

There are a number of different date formats used around the world, and the approach for changing to any of them is broadly the same. In this tutorial we'll show how to change from the default US format (mm/dd/yyyy) to the dd/mm/yyyy format used in most other English-speaking countries and those speaking many other languages. As date formats are generally language-specific (or in the case of English, dialect-specific) we'll be editing two Zen Cart language files to make this change.  

If you are looking for the instructions for versions prior to Zen Cart 1.5.8, please see [Date format for 1.5.7 and below](/user/localization/changing_date_format_157/). 


# Instructions for 1.5.8 and above 

### 1. Open file `includes/languages/YOURTEMPLATE/lang.YOURLANGUAGE.php`

(if this file doesn't exist, create it by copying the file `includes/languages/lang.YOURLANGUAGE.php` to this location).  

### 1a. find this line

```
$locales = ['en_US', 'en_US.utf8', 'en', 'English_United States.1252'];
```
and replace with:  

```
$locales = ['en_GB', 'en_GB.utf8', 'en']
```

### 1b. find these lines 

```
    'DATE_FORMAT' => 'm/d/Y',

    'DOB_FORMAT_STRING' => 'mm/dd/yyyy',
```

and replace with:  

```
    'DATE_FORMAT' => 'd/m/Y',

    'DOB_FORMAT_STRING' => 'dd/mm/yyyy',
```

### 1c. find these lines 

```
    'ENTRY_DATE_OF_BIRTH_ERROR' => 'Is your birth date correct? Our system requires the date in this format: MM/DD/YYYY (eg 05/21/1970) or this format: YYYY-MM-DD (eg 1970-05-21)',
    'ENTRY_DATE_OF_BIRTH_TEXT' => '* (eg. 05/21/1970 or 1970-05-21)',
```

and replace with:  

```
    'ENTRY_DATE_OF_BIRTH_ERROR' => 'Is your birth date correct? Our system requires the date in this format: DD/MM/YYYY (eg 21/05/1970) or this format: YYYY-MM-DD (eg 1970-05-21)',
    'ENTRY_DATE_OF_BIRTH_TEXT' => '* (eg. 21/05/1970 or 1970-05-21)',
```

### 2. Open file `includes/functions/functions_dates.php`

### 2a. find `zen_date_raw`

change
```
    if ($reverse) {

      return substr($date, 3, 2) . substr($date, 0, 2) . substr($date, 6, 4);

    } else {

      return substr($date, 6, 4) . substr($date, 0, 2) . substr($date, 3, 2);

    }

  }

}
```

to: 

```
    if ($reverse) {

      return substr($date, 0, 2) . substr($date, 3, 2) . substr($date, 6, 4);

    } else {

      return substr($date, 6, 4) . substr($date, 3, 2) . substr($date, 0, 2);

    }

  }

}  
```



### 3. Open file `admin/includes/languages/lang.YOURLANGUAGE.php`

(this file cannot be over-ridden at present, so you will need to edit the file directly and be careful to reapply the changes if you upgrade to a later version of Zen Cart)  


### 3a. Perform the same change as you did in 1a.

### 3b. find these lines 
```
    'DATE_FORMAT' => 'm/d/Y',
    'DATE_FORMAT_SHORT' => '%m/%d/%Y',
    'DATE_FORMAT_SPIFFYCAL' => 'MM/dd/yyyy',
```

and replace with 

```
    'DATE_FORMAT' => 'd/m/Y',
    'DATE_FORMAT_SHORT' => '%d/%m/%Y',
    'DATE_FORMAT_SPIFFYCAL' => 'dd/MM/yyyy',
```

### 3c. find these lines

```
    'ENTRY_DATE_OF_BIRTH_ERROR' => '&nbsp;<span class="errorText">(eg. 05/21/1970)</span>',
```

and replace with

```
    'ENTRY_DATE_OF_BIRTH_ERROR' => '&nbsp;<span class="errorText">(eg. 21/05/1970)</span>',
```

### 3d. find these lines

```
    'PHP_DATE_TIME_FORMAT' => 'm/d/Y H:i:s',
```

and replace with

```
    'PHP_DATE_TIME_FORMAT' => 'd/m/Y H:i:s',
```

And that's it, you're done!  

