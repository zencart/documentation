# Admin Request Sanitization

## Introduction 

We have introduced a new sanitization class into v1.5.5 which takes a much more agressive stance than previous code. 
The new code is likely to have an affect on plugins that add or change admin functionality.
To mitigate this some overrides and switches have been allowed for. This documentation should allow plugin authors and 
sites that already use plugins to workaround potential problems.

The new code introduces a number of sanitization groups, each group performs a specific sanitization on specific GET/POST 
parameters.For GET/POST parameters that are not already sanitized within these groups we then run a default sanitization 
htmlspecialchars).

It is this last default sanitization that may potentially break 3rd party plugins.

## Disabling Strict Sanitization

If you find that some of your admin plugins are no longer working properly then you should look first to see if new 
versions of those plugins are available, that support the new v155 sanitization. 

If new versions are not available, or you need to keep your current admin working while you update, then you can disable
the strict(default) sanitization by doing the following.

Create a new disable_strict_sanitize.php file in your admin/includes/extra_configures directory.
The contents of this file should be 

<?php
define('DO_STRICT_SANITIZATION', false);


## For Developers. How to use the sanitization in plugins.

If you are a developer who wants to update their curerent code, or you are developing a new plugin, here are some tips to
keep your plugin compatible with v1.5.5 code.


### Parameter naming

### Default Sanitization Groups

### Custom Sanitizers 


