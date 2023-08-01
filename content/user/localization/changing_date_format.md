---
title: Date format - changing it from the US format to dd/mm/yyyy (1.5.8+)
description: Localizing data display 
category: localization
weight: 10
---

**NOTE:** These instructions are for Zen Cart 1.5.8 and above.  If you are looking for the instructions for versions prior to Zen Cart 1.5.8, please see [Date format for 1.5.7 and below](/user/localization/changing_date_format_157/). 

There are a number of different date formats used around the world, and the approach for changing to any of them is broadly the same. In this tutorial we'll show how to change from the default US format (mm/dd/yyyy) to the dd/mm/yyyy format used in most other English-speaking countries and those speaking many other languages. As date formats are generally language-specific (or in the case of English, dialect-specific) we'll be editing two Zen Cart language files to make this change.  

# Instructions for 1.5.8 and above 

### 1. Open file `includes/languages/YOURTEMPLATE/lang.YOURLANGUAGE.php`

(if this file doesn't exist, create it by copying the file `includes/languages/lang.YOURLANGUAGE.php` to this location).  

### 1a. find this line

```
$locales = ['en_US', 'en_US.utf8', 'en', 'English_United States.1252'];
```
and replace with:  

```
$locales = ['en_GB', 'en_GB.utf8', 'en'];
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

### 2. Open file `includes/functions/functions_dates.php` NB. As of version 1.5.8a this step is not necessary go straight to [step 3](#3-create-file-adminincludeslanguagesenglishextra_definitionslangadmin_overridesphp)

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



### 3. Create file `admin/includes/languages/english/extra_definitions/lang.admin_overrides.php`

(if it already exists simply add the lines below excluding the first line `<?php` )

### 3a. insert the following lines

```
<?php
@setlocale(LC_TIME, ['en_GB', 'en_GB.utf8', 'en']);

$define['DATE_FORMAT'] = 'd/m/Y';
$define['DATE_FORMAT_SHORT'] = '%d/%m/%Y';
$define['DATE_FORMAT_SPIFFYCAL'] = 'dd/MM/yyyy';
$define['ENTRY_DATE_OF_BIRTH_ERROR'] = '&nbsp;<span class="errorText">(eg. 21/05/1970)</span>';
$define['PHP_DATE_TIME_FORMAT'] = 'd/m/Y H:i:s';

return $define;

```

And that's it, you're done!  

