---
title: Admin Request Sanitization
description: How data is sanitized on the admin side 
weight: 1
---

The Admin Sanitization features use a number of sanitization groups. Each group performs a sanitization on specific GET/POST parameters. 
For GET/POST parameters that are not already sanitized within these groups we then run a default sanitization 
(i.e.: simply running `htmlspecialchars()` on it).

## Why Sanitize?

Historically, weaker sanitization was used for two reasons:

Firstly, Admin allows lots of parameters to include what would be considered dangerous characters. 
e.g. product descriptions allow script tags, and other inputs allow some html, such as product names.

Secondly, core code uses CSRF tokens for all form interactions. The use of these tokens mitigates against any exploiting of XSS, unless an admin session is already available. 

However, reports such as https://www.trustwave.com/Resources/SpiderLabs-Blog/TWSL2016-006--Multiple-XSS-Vulnerabilities-reported-for-Zen-Cart/
made us reconsider. 
While we still contend that the CSRF protection mitigates these supposed XSS vulnerabilities, there are three good reasons to address them with extra sanitization:

1. We cannot guarantee that 3rd party plugins use the CSRF token system (although there are some safeties to ensure they do).

2. PCI scanning software may detect XSS vulnerabilities, even given the CSRF mitigation. (particularly where the scanner bypasses/grants admin logins)

3. Good security practice.


## TEMPORARILY Disabling Strict Sanitization

If you find that some of your pre-v1.5.5 admin plugins are no longer working properly then you should look first to see if new 
versions of those plugins are available, i.e.: that support the sanitization methods implemented since v1.5.5. 

If new versions are not available, or you need to keep your current admin working while you update, then you can disable
the strict(default) sanitization by doing the following:

Create a new `disable_strict_sanitize.php` file in your `/admin/includes/extra_configures/` directory.
The contents of this file should be 

```
  <?php
  define('DO_STRICT_SANITIZATION', false);
```

We encourage you to NOT do that unless truly necessary, and even then only as a temporary measure until your affected plugins have written their own custom sanitizers as described later in this document.

## Logging

The AdminSanitizer class can log the actions it takes, and this may be helpful in debugging problems with plugins.

Logging is enabled/disabled using the DO_DEBUG_SANITIZATION define.

To enable logging create a new file in `/admin/includes/extra_configures/` that contains 

```
  <?php
  define('DO_DEBUG_SANITIZATION', true);
```

## For Developers. How to use the sanitization in plugins.

If you are a developer who wants to update your current code, or you are developing a new plugin, the following
are some tips to keep your plugin compatible with core functionality.


### Parameter Naming

GET/POST parameters will be sanitized based on their parameter name and the sanitization group assigned to them. 
Therefore, if you are writing a plugin and use a parameter name that already exists in Zen Cart that parameter will be 
sanitized according to the group it is already assigned to in core code. 

For example, the `action` parameter is assigned to the `SIMPLE_ALPHANUM_PLUS` group, and the sanitization for that group 
will always be applied to it.

There will be occasions where a plugin uses a parameter name that is already added to a sanitization group, and rewriting
 plugin code may be onerous. For these cases it is possible to override sanitization on a per page basis.


### Adding Parameters/Groups

If a plugin needs to define its own sanitization or override the sanitization for an already defined parameter, it 
should create a php file in `/admin/includes/extra_datafiles/`

An example of the contents might be 

    $sanitizer = AdminRequestSanitizer::getInstance();
    $group = array(
        'id' => array('sanitizerType' => 'CONVERT_INT', 'method' => 'both', 'pages' => array('edit_orders'), 'params' => array()),
        );
    $sanitizer->addComplexSanitization($group);

or

    $sanitizer = AdminRequestSanitizer::getInstance();
    $group = array(
      'col_html_text' => array('sanitizerType' => 'PRODUCT_DESC_REGEX', 'method' => 'post'),
        );
    $sanitizer->addComplexSanitization($group);



The structure of the defining array is:

1. sanitizerType = The name of a sanitizer group (see the group names below) 
2. method = get|post|both
3. pages = (optional) an array of pages which this sanitizer rule will be applied to; (if not supplied, will apply to all pages)
4. params = (optional) this is used only for the MULTI_DIMENSIONAL sanitizer, which is explained below.

Here's a specific example from the [News Box Manager](https://www.zen-cart.com/downloads.php?do=file&id=2264) plugin.  The file `admin/includes/extra_datafiles/news_box_manager_sanitization.php` sanitizes the fields `news_title` and `news_content` when they are updated: 

```
if (class_exists('AdminRequestSanitizer') && method_exists('AdminRequestSanitizer', 'getInstance')) {
    $news_mgr_sanitizer = AdminRequestSanitizer::getInstance();
    $news_mgr_sanitizer->addSimpleSanitization('PRODUCT_DESC_REGEX', array('news_title', 'news_content'));
}
```

The `pages` parameter is not specified here because this particular plugin 
is designed for easy extension, so that pages can be added simply by copying a single file (and requiring someone to modify this file as well 
to add the new page would be contrary to that intention.)


### General Sanitization Groups

Zen Cart defines the following default case-insensitive sanitizers:

+ `SIMPLE_ALPHANUM_PLUS`

    GET and POST Values
    
    Uses `[^\/ 0-9a-zA-Z_:@.-]` regex
      
      
+ `CONVERT_INT`

    GET and POST values
    
    converts value to Integer
    
+ `FILE_DIR_REGEX`

    POST values only 
    
    uses ``[^0-9a-z.!@#$%^&()_-~`+^ \\]`` regex

    
+ `ALPHANUM_DASH_UNDERSCORE`

    GET and POST values
    
    Uses `[^a-z0-9_-]` regex
    
    
+ `WORDS_AND_SYMBOLS_REGEX`

    GET and POST values
    
    Uses `(<\/?scri|on(load|mouse|error|read|key)(up|down)? ?=|[^(class|style)] ?= ?(\(|")|<!)` regex
    
    
+ `META_TAGS`

    POST Values only (Deep)
    
    Uses `htmlspecialchars($_POST[$parameterName][$pKey], ENT_COMPAT, $this->charset, false)`
    
    
+ `SANITIZE_EMAIL`

    GET and POST values
    
    Uses `filter_var($_POST[$key], FILTER_SANITIZE_EMAIL)`
    
+ `SANITIZE_EMAIL_AUDIENCE`

    POST values only
    
    Uses `htmlspecialchars($_POST[$parameterName], ENT_COMPAT, $this->charset, true)`

+ `PRODUCT_URL_REGEX`

    POST values only (Deep)
    
    Uses `([^0-9a-z'.!@#$%&()_-~/;:=?[]]|[><])` regex
    
+ `PRODUCT_DESC_REGEX`

    POST Values only (Deep)
    
    Uses `(load=|= ?\(|<![^-])` regex
    
    
+ `CURRENCY_VALUE_REGEX`

    POST Values only
    
    Uses `[^a-z0-9_,\.\-]` regex


+ `FLOAT_VALUE_REGEX`

    POST Values only
    
    Uses `[^0-9,\.\-\+]` regex

+ `PRODUCT_NAME_DEEP_REGEX`

    POST Values only (Deep)
    
    Uses `(<\/?scri|on(load|mouse|error|read|key)(up|down)? ?=|[^(class|style)] ?= ?(\(|")|<!)` regex
    
+ `NULL_ACTION`

    GET/POST Values
    
    Skips sanitization for the relevant parameter.

+ `STRICT_SANITIZE_VALUES`

    Any parameters not previously sanitized will be sanitized with this method. 


+ `STRICT_SANITIZE_KEYS`

	All POST and GET "keys" containing any `<` or `>` symbols in the key will be `unset()`


### MULTI_DIMENSIONAL Sanitization

The MULTI_DIMENSIONAL sanitizer is special in that it defines sanitization for an array of parameters, rather
than one parameter as other sanitizers do.

For example, if you post the following array 

    [update_products] => Array
        (
            [13] => Array
                (
                    [qty] => 1
                    [name] => Microsoft IntelliMouse Explorer
                    [onetime_charges] => 0.0000
                    [attr] => Array
                        (
                            [3] => Array
                                (
                                    [value] => 11
                                    [type] => 0
                                )

                        )

                    [model] => MSIMEXP
                    [tax] => 0
                    [final_price] => 70.95  

normal sanitizers would only address the outer `update_products` parameter, while what you really want to do is define 
parameters for `qty` `name` `onetime_charges` etc, and you also want to sanitize the attr sub array recursively.

to address this, you can define a MULTI_DIMENSIONAL sanitizer like this:-

    $sanitizer = AdminRequestSanitizer::getInstance();
    $group = array(
        'update_products' => array(
            'sanitizerType' => 'MULTI_DIMENSIONAL',
            'method' => 'post',
            'pages' => array('edit_orders'),
            'params' => array(
                'update_products' => array('sanitizerType' => 'CONVERT_INT'),
                'qty' => array('sanitizerType' => 'CONVERT_INT'),
                'name' => array('sanitizerType' => 'WORDS_AND_SYMBOLS_REGEX'),
                'onetime_charges' => array('sanitizerType' => 'CURRENCY_VALUE_REGEX'),
                'attr' => array(
                    'sanitizerType' => 'MULTI_DIMENSIONAL',
                    'params' => array(
                        'attr' => array('sanitizerType' => 'CONVERT_INT'),
                        'value' => array('sanitizerType' => 'CONVERT_INT'),
                        'type' => array('sanitizerType' => 'CONVERT_INT')
                    )
                ),
                'model' => array('sanitizerType' => 'WORDS_AND_SYMBOLS_REGEX'),
                'tax' => array('sanitizerType' => 'WORDS_AND_SYMBOLS_REGEX'),
                'final_price' => array('sanitizerType' => 'WORDS_AND_SYMBOLS_REGEX'),
            )
        )
    );
    $sanitizer->addComplexSanitization($group);

Note that sanitizers for sub parameters are defined in the `params` array and that you can recursively define 
deeper arrays with a further MULTI_DIMENSIONAL sanitizer array.


### Custom Sanitizers 

tbd


