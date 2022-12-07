---
title: configure.php explained 
description: Understanding the main Zen Cart configuration file
category: miscellaneous
weight: 1 
---


**Quick Summary:**

`HTTP_SERVER` is the domain name of your site (eg: `https://www.YOURSITE.com`). Visiting this URL will take customers to the "webroot" of your domain, whether or not your store is located in that spot.  

`DIR_WS_CATALOG` and `DIR_WS_HTTPS_CATALOG` are the subdirectory foldernames that must be added to the URL in order to take customers to your store. 

If your store is located in the [webroot](/user/first_steps/how_do_i_install#what-is-my-webroot), then simply entering `'/'` here will suffice. 

But if your store is located in a subdirectory like `www.YOURSITE.com/store/` then it would be necessary to see `'/store/'` as the value here.  

Explained another way: Zen Cart builds its URLs by combining two values from your configure.php files: 

`HTTP_SERVER` plus `DIR_WS_CATALOG` plus the page portion of the URL  
and
`HTTPS_SERVER` plus `DIR_WS_HTTPS_CATALOG` plus the page portion of the URL  

ie: `http://www.MYSITE.com` plus `/store/` and then whatever the address is to the page requested, such as `index.php?main_page=shopping_cart`.

So, if your settings for those values point to the wrong place, you'll instantly see that reflected in the URLs you click on when you first arrive at the site. Using that information you should be able to reverse-engineer the URL you see in your browser to break it down into the parts that go into both places.  
  
> Tip: setting `HTTP_SERVER` to a URL starting with `https://` means all your pages will be handled using SSL. This *is* a desired effect.  (In this sort of situation, you can also set HTTPS_SERVER to whatever HTTP_SERVER is using, and DIR_WS_HTTPS_CATALOG to whatever DIR_WS_CATALOG is using.)

Of course SSL urls will only work properly if you actually have SSL available on your site, with a valid SSL certificate. Talk to your hosting company about proper SSL certificate configuration for your domain and hosting account.


**PATHS:**  

`DIR_FS_CATALOG` points to the physical file folder path on the server. If you're only changing the URL of your site and not actually changing the foldername where the site sits, then you don't need to touch this.  

However, keep in mind that there IS a similarity between `DIR_WS_CATALOG` and `DIR_FS_CATALOG`:  

`DIR_FS_CATALOG` might read: `/home/myname/public_html/store/` 
and thus `DIR_WS_CATALOG` is: `/store/`

(`DIR_WS_CATALOG` points to whatever follows the [webroot](/user/first_steps/how_do_i_install#what-is-my-webroot), configuration of your hosting account, 
ie: which folder your account points to for your actual site.  In most cases this folder is named `public_html` or `htdocs` or `httpdocs`)  

**Other Paths:**

The following paths RARELY require changing, and only when doing advanced alterations in how files are stored on your server. Best not to change them unless you first study exactly what the changed effect will be.

(In fact, it is rare to see these in your configure.php file at all, unless you are intentionally overriding normal definition or are using a very old version of Zen Cart where these were not centrally defined away from common editing.)

```
define('DIR_WS_IMAGES', 'images/');  
define('DIR_WS_DOWNLOAD_PUBLIC', DIR_WS_CATALOG . 'pub/');  
define('DIR_WS_TEMPLATES', DIR_WS_INCLUDES . 'templates/');  
define('DIR_WS_UPLOADS', DIR_WS_IMAGES . 'uploads/');  
define('DIR_FS_UPLOADS', DIR_FS_CATALOG . DIR_WS_UPLOADS);  
define('DIR_FS_EMAIL_TEMPLATES', DIR_FS_CATALOG . 'email/');  
define('DIR_FS_DOWNLOAD_PUBLIC', DIR_FS_CATALOG . 'pub/');  
```

The following line might be changed by a storeowner who sells downloadable items and wants to secure the originals from theft. Substituting the 'DIR_FS_CATALOG' portion of this value with an alternate path, after relocating the physical folder to the corresponding location, would be the method used to accomplish this. There is another FAQ article on this specific topic.  

`define('DIR_FS_DOWNLOAD', DIR_FS_CATALOG . 'download/');`


**DATABASE SETTINGS**  
```
define('DB_TYPE', 'mysql');  
```
In Zen Cart, the only valid value for this is 'mysql'.  

```
define('DB_PREFIX', ''); // prefix for database table names -- preferred to be left empty  
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

This is the collation or character set that Zen Cart tells MySQL to use when exchanging database data back and forth.
While `utf8` is common, using `utf8mb4` enables support for emojis and other multibyte characters. 
However, changing this setting must be done before first install, or else you must manually update all the table fields in your database after changing it here.

See [this article](/user/upgrading/detailed_upgrading/#character-set) for more details on character set. 

See [this article](/user/upgrading/convert_to_utf8) for a utility which can help you convert your database from `latin1`/`iso-8859-1` to `utf8`. 

```
define('DB_SERVER', 'localhost');  
```

This is the address to the server which runs your database. In most cases 'localhost' is the correct choice. Your hosting company can tell you if it should be something else. In some cases (or if using `Docker` or other container services) you might require `127.0.0.1` instead of `localhost`.

```
define('DB_SERVER_USERNAME', 'your username');  
define('DB_SERVER_PASSWORD', 'your password');  
define('DB_DATABASE', 'your assigned databasename');  
```

These settings are selected by you when you create the database for your store. In some cases they might be assigned for you by an automated database-creation feature in your hosting company's control panel. Usually you are able to select them yourself. Sometimes the username and databasename have your hosting account name added at the beginning, e.g. `yourname_dbname123` even though you selected just `dbname123`. Your hosting company's control panel will show you this if it makes this alteration for you.

**OTHER SETTINGS (Advanced)**  

```
define('SQL_CACHE_METHOD', 'none');  
```
Choices are `file`, `none`, or `database`. Choosing other than `none` will allow some database queries to be cached to avoid re-running the query for a full set of results. For larger complex queries this can speed performance.

```
define('DIR_FS_SQL_CACHE', '/enter/your/path/to/public_html_or_htdocs/and/zencart/here/zen/cache');  
```

This setting specifies the path where SQL cache files would be stored if 'file' mode is selected. 

(In v1.3.9 and v1.5.0, this setting was ALSO used for storing various debug logs used for troubleshooting problems your PHP scripts might be having in your store. As of v1.5.1, these logs are now found in the `DIR_FS_LOGS` location (see below).)

It's possible to relocate this folder to another location perhaps outside your site's [webroot](/user/first_steps/how_do_i_install#what-is-my-webroot), for increased security. 
Simply relocate the folder using your [FTP tool](/user/first_steps/useful_tools/#ftp-tools), and adjust this value to match the new location.  

```
define('DIR_FS_LOGS', '/enter/your/path/to/public_html_or_htdocs/and/zencart/here/zen/logs');  
```

`DIR_FS_LOGS` specifies the path where to store various debug logs used for troubleshooting problems your PHP scripts might be having in your store.
It's possible to relocate this folder to another location perhaps outside your site's [webroot](/user/first_steps/how_do_i_install#what-is-my-webroot), for increased security. 
Simply relocate the folder using your FTP program, and adjust this value to match the new location.  

See also [What is STRICT mode for my database](/user/troubleshooting/db_strict_mode/) for information on `DB_MYSQL_MODE`. 

