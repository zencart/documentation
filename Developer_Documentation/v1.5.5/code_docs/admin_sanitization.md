# Admin Request Sanitization

## Introduction 

We have introduced a new sanitization class into v1.5.5 which takes a much more agressive stance than previous code. 

The new code is likely to have an affect on plugins that add or change admin functionality. To mitigate this some 
overrides and switches have been allowed for. This documentation should allow plugin authors and sites that 
already use plugins to workaround potential problems.

The new code introduces a number of sanitization groups. Each group performs a specific sanitization on specific GET/POST 
parameters. For GET/POST parameters that are not already sanitized within these groups we then run a 
default sanitization (simply running `htmlspecialchars()` on it).

It is this last default sanitization that may potentially break 3rd-party plugins.

## Disabling Strict Sanitization

If you find that some of your admin plugins are no longer working properly then you should look first to see if new 
versions of those plugins are available, ie: that support the new v1.5.5 sanitization. 

If new versions are not available, or you need to keep your current admin working while you update, then you can disable
the strict(default) sanitization by doing the following:

Create a new `disable_strict_sanitize.php` file in your `/admin/includes/extra_configures/` directory.
The contents of this file should be 
```
  <?php
  define('DO_STRICT_SANITIZATION', false);
```
We encourage you to NOT do that unless truly necessary, and even then only as a temporary measure until your affected plugins have written their own custom sanitizers as described later in this document.


## For Developers. How to use the sanitization in plugins.

If you are a developer who wants to update your current code, or you are developing a new plugin, the following
are some tips to keep your plugin compatible with v1.5.5 core functionality.


### Parameter naming

GET/POST parameters will be sanitized based on their parameter name and the sanitization group assingned to them. 
Therefore if you are writing a plugin and use a parameter name that already exists in Zen Cart that parameter will be 
sanitized according to the group it is already assigned to in core code. 

For example the `action` parameter is assigned to the `SIMPLE_ALPHANUM_PLUS` group, and the sanitization for that group 
will always be applied to it, even if you were to use that parameter in a way that requires different treatment.

You should therefore be careful in naming the GET/POST parameters that your plugin uses.

### Default Sanitization Groups

Zen Cart defines the following default case-insensitive sanitizers:

+ `SIMPLE_ALPHANUM_PLUS`

    GET Values only
    
    Uses `[^\/ 0-9a-zA-Z_:@.-]` regex
      
      
+ `CONVERT_INT`

    GET and POST values
    
    converts value to Integer
    
+ `FILE_DIR_REGEX`

    POST values only 
    
    uses `[^0-9a-z.!@#$%^& ()`_+-~/\\]` regex

    
+ `ALPHANUM_DASH_UNDERSCORE`

    GET and POST values
    
    Uses `[^a-z0-9_-]` regex
    
    
+ `WORDS_AND_SYMBOLS_REGEX`

    GET and POST values
    
    Uses `(<\/?scri|on(load|mouse|error|read|key)(up|down)? ?=|[^(class|style)] ?= ?(\(|")|<!)` regex
    
    
+ `META_TAGS`

    POST Values only (Deep)
    
    Uses `(load=|= ?\(|<![^-])` regex
    
    
+ `SANITIZE_EMAIL`

    GET and POST values
    
    Uses `filter_var($_POST[$key], FILTER_SANITIZE_EMAIL)`


+ `PRODUCT_DESC_REGEX`

    POST Values only (Deep)
    
    Uses `(load=|= ?\(|<![^-])` regex
    
    
+ `WORDS_AND_SYMBOLS_REGEX`

    POST Values only (Deep)
    
    Uses `([^a-z0-9\'!#$&%@();:/=?_\~\[\]-]|[><])` regex
    
    
+ `CURRENCY_VALUE_REGEX`

    POST Values only
    
    Uses `[^a-z0-9_,\.\-]` regex


+ `PRODUCT_NAME_DEEP_REGEX`

    POST Values only (Deep)
    
    Uses `(<\/?scri|on(load|mouse|error|read|key)(up|down)? ?=|[^(class|style)] ?= ?(\(|")|<!)` regex
    

+ `STRICT_SANITIZE_VALUES`

    Any parameters not previously sanitized will be sanitized with this method. Although you can pass a list of parameters
    not to sanitize. 


+ `STRICT_SANITIZE_KEYS`

	All POST and GET "keys" containing any `<` or `>` symbols in the key will be `unset()`


### Custom Sanitizers 

### Overriding Default Sanitization Group Entries


