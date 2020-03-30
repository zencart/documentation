---
title: configure.php explained 
description: Zen Cart configure.php explained 
category: miscellaneous
weight: 1 
---

FIXME add details about running entire site in SSL

**Quick Summary:**

`HTTP_SERVER` and `HTTPS_SERVER` are the domain name of your site. Visiting this URL will take customers to the "webroot" of your domain, whether or not your store is located in that spot.  

`DIR_WS_CATALOG` and `DIR_WS_HTTPS_CATALOG` are the foldernames that must be added to the URL in order to take customers to your store. If your store is located in the 
 [webroot](/user/first_steps/how_do_i_install#what-is-my-webroot), 
then simply entering '/' here will suffice. But if your store is located in a subdirectory like `www.YOURSITE.com/store/` then it would be necessary to see /store/ as the value here.  

Explained another way: Zen Cart builds its URLs by combining two values from your configure.php files:  

**NON-SSL pages:**

`HTTP_SERVER` plus `DIR_WS_CATALOG` plus the page portion of the URL  

ie: `http://www.MYSITE.com` plus `/store/` and then whatever the address is to the page requested, such as `index.php?main_page=shopping_cart`.

So, if your settings for those values point to the wrong place, you'll instantly see that reflected in the URLs you click on when you first arrive at the site. Using that information you should be able to reverse-engineer the URL you see in your browser to break it down into the parts that go into both places.  
  
Tip: In your Admin configure.php, if you set your HTTP_SERVER to a URL starting with https:// then all your admin pages will be handled using SSL. This *is* a desired effect on the Admin side.  

Of course SSL urls will only work properly if you actually have SSL available on your site, with a valid certificate.

**SSL pages:**  

SSL links/URLs are built similarly:  

`HTTPS_SERVER` plus `DIR_WS_HTTPS_CATALOG` plus the page portion of the URL  
ie: `http://www.MYSITE.com` plus `/store/` and then whatever the address is to the page requested, such as `index.php?main_page=login`.

**PATHS:**  

`DIR_FS_CATALOG` points to the physical file folder path on the server. If you're only changing the URL of your site and not actually changing the foldername where the site sits, then you don't need to touch this.  

However, keep in mind that there IS a similarity between `DIR_WS_CATALOG` and `DIR_FS_CATALOG`:  

`DIR_FS_CATALOG` might read: `/home/myname/public_html/store/` 
and thus `DIR_WS_CATALOG` is: `/store/`

(`DIR_WS_CATALOG` points to whatever follows the 
[webroot](/user/first_steps/how_do_i_install#what-is-my-webroot), 
configuration of your hosting account, ie: which folder your account points to for your actual site ... in most cases this folder is named "public_html" or "htdocs" or "httpdocs")  

**Other Paths:**

The following paths should NOT be changed. It is VERY rare to ever need to change any of these. Changing them will result in breaking normal operation of your site.  
```
define('DIR_WS_IMAGES', 'images/');  
define('DIR_WS_INCLUDES', 'includes/');  
define('DIR_WS_FUNCTIONS', DIR_WS_INCLUDES . 'functions/');  
define('DIR_WS_CLASSES', DIR_WS_INCLUDES . 'classes/');  
define('DIR_WS_MODULES', DIR_WS_INCLUDES . 'modules/');  
define('DIR_WS_LANGUAGES', DIR_WS_INCLUDES . 'languages/');  
define('DIR_WS_DOWNLOAD_PUBLIC', DIR_WS_CATALOG . 'pub/');  
define('DIR_WS_TEMPLATES', DIR_WS_INCLUDES . 'templates/');  
define('DIR_WS_UPLOADS', DIR_WS_IMAGES . 'uploads/');  
define('DIR_FS_UPLOADS', DIR_FS_CATALOG . DIR_WS_UPLOADS);  
define('DIR_FS_EMAIL_TEMPLATES', DIR_FS_CATALOG . 'email/');  
define('DIR_FS_DOWNLOAD_PUBLIC', DIR_FS_CATALOG . 'pub/');  
```

The following line might be changed by a storeowner who sells downloadable items and wants to secure the originals from theft. Substituting the 'DIR_FS_CATALOG' portion of this value with an alternate path, after relocating the physical folder to the corresponding location, would be the method used to accomplish this. There is another FAQ article on this specific topic.  
define('DIR_FS_DOWNLOAD', DIR_FS_CATALOG . 'download/');  

**DATABASE SETTINGS**  
```
define('DB_TYPE', 'mysql');  
```
In Zen Cart, the only valid value for this is 'mysql'.  

```
define('**DB_PREFIX**', ''); // prefix for database table names -- preferred to be left empty  
```
The prefix is used only when your hosting server's configuration allows you only a single database in your hosting account, and is an undesired workaround to allow multiple software applications to share the same database without clashing tablenames.  
Ideally you will leave this blank, as shown here.  
Some hosting companies offering "one-click installs" (which are NOT recommended by Zen Cart) will stuff `zen_` in there as a prefix. This can create all kinds of confusion when you try moving your site to another server and forget (or don't know) that the prefix has been set and all your tablenames were altered.  

Here's an example of what using `DB_PREFIX` does in your database:  

<table width="400" align="left" class="cms_table">

<tbody>

<tr valign="top" class="cms_table_tr" style="background-color: yellow">

<td class="cms_table_td">**no prefix**</td>

<td class="cms_table_td">**'zen_' prefix**</td>

<td class="cms_table_td">**'fred_' prefix**</td>

</tr>

<tr valign="top" class="cms_table_tr">

<td class="cms_table_td">address_book</td>

<td class="cms_table_td">zen_address_book</td>

<td class="cms_table_td">fred_address_book</td>

</tr>

<tr valign="top" class="cms_table_tr">

<td class="cms_table_td">countries</td>

<td class="cms_table_td">zen_countries</td>

<td class="cms_table_td">fred_countries</td>

</tr>

<tr valign="top" class="cms_table_tr">

<td class="cms_table_td">products</td>

<td class="cms_table_td">zen_products</td>

<td class="cms_table_td">fred_products</td>

</tr>

</tbody>

</table>


```
define('DB_CHARSET', 'utf8');  
```

This is the collation or character set that Zen Cart asks MySQL to use when exchanging database back and forth. Another, but older, common choice instead of utf8 is latin1.  

```
define('DB_SERVER', 'localhost');  
```

This is the address to the server which runs your database. In most cases 'localhost' is the correct choice. Your hosting company can tell you if it should be something else.  

```
define('DB_SERVER_USERNAME', 'your username');  
define('DB_SERVER_PASSWORD', 'your password');  
define('DB_DATABASE', 'your assigned databasename');  
```

These settings are selected by you when you create the database for your store. In some cases they might be assigned for you by an automated database-creation feature in your hosting company's control panel. Usually you are able to select them yourself. Sometimes the username and databasename have your hosting account name added at the beginning, e.g. `yourname_dbname123` even though you selected just `dbname123`. Your hosting company's control panel will show you this if it makes this alteration for you.  

**OTHER SETTINGS (Advanced)**  

```
define('**SQL_CACHE_METHOD**', 'none');  
```
It is recommended to set this to 'none' or 'database' for optimum performance.  
Alternatively, setting it to 'file' might offer minor improvements if the webserver is very slow and poorly configured. In this case it's better to move to a more reliable server instead of using the 'file' method.  
Additionally, if choosing to use the 'file' method, you MUST relocate the SQL CACHE folder outside your webroot as described below, else you open yourself up to security risks.  

**NOTE:** As of v1.5.0, the "file" option is obsolete. Only 'none' or 'database' have any meaning.  

```
define('DIR_FS_SQL_CACHE', '/enter/your/path/to/public_html_or_htdocs/and/zencart/here/zen/cache');  
```

This setting specifies the path where SQL cache files would be stored if 'file' mode is selected. In v1.3.9 and v1.5.0, this setting was ALSO used for storing various debug logs used for troubleshooting problems your PHP scripts might be having in your store. As of v1.5.1, these logs are now found in the `DIR_FS_LOGS` location (see below).  

It's possible to relocate this folder to another location perhaps outside your site's webroot, for increased security. Simply relocate the folder using your [FTP tool](/user/first_steps/useful_tools/#ftp-tools), and adjust this value to match the new location.  
For more information on understanding "webroot" concepts, see your favorite search engine.  

```
define('DIR_FS_LOGS', '/enter/your/path/to/public_html_or_htdocs/and/zencart/here/zen/logs');  
```

In Zen Cart v1.5.1 and newer, this setting specifies the path where the program can store various debug logs used for troubleshooting problems your PHP scripts might be having in your store.  
It's possible to relocate this folder to another location perhaps outside your site's webroot, for increased security. Simply relocate the folder using your FTP program, and adjust this value to match the new location.  

See also [What is STRICT mode for my database](/user/troubleshooting/db_strict_mode) for information on `DB_MYSQL_MODE`. 

For more information on understanding "webroot" concepts, see 
[webroot](/user/first_steps/how_do_i_install#what-is-my-webroot) or 
your favorite search engine.

