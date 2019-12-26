Multi Language Configuration Menus
==================================



In v2, you can now have multilanguage Configuration menu entries.  However, the creation of the language strings for the Configuration menu is done differently from the regular way other strings in a language pack are created.

To add strings for your a new language for the Configuration Menu, look up the database entry in the zc_install/sql/install/mysql_zencart.sql file. 


For example, the strings used to set the Store Name in Configuration->My Store->Store Name are associated with database key STORE_NAME.
To create non-english equivalents for these strings, create or edit the file 

admin/includes/languages/your-language/configuration.php

and preface the key with CFGTITLE_ to set the title and CFGDESC to set the description.  So using the STORE_NAME example again, 

``` 
define('CFGTITLE_STORE_NAME', 'Nombre de la Tienda');
define('CFGDESC_STORE_NAME', 'El nombre de mi tienda');
```
