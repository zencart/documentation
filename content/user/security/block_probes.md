---
title: Blocking probing activity 
description: Stopping robots and other pests 
category: security
weight: 10
---

Some common attempts to probe your site for old vulnerabilities, or vulnerabilities from other systems, can be blocked by adding the following code to your site:  
1\. Copy and paste the following code into a new text file in your favorite text-only editor.  
2\. Save the file as `block_probing.php`, and upload it to your store into the following folders:  

a) `/YOURADMIN/includes/extra_configures/  `

b) `/includes/extra_configures/  `

```
<?php
/**
 * @package security
 * @copyright Copyright 2003-2011 Zen Cart Development Team
 * @license [https://www.zen-cart.com/license/2_0.txt](https://www.zen-cart.com/license/2_0.txt) GNU Public License V2.0
 * @copyright Portions Copyright 2008,2009,2010,2011 GNU/GPL V.2 BY MIKE H. [HTTP://WWW.SPAMBOTSECURITY.COM](HTTP://WWW.SPAMBOTSECURITY.COM)
 * @version $Id: vuln_trap.php 15882 2011-09-01 08:23:55Z drbyte $
 */
$paramsToCheck = array();

// List of strings to search for and block
$paramsToCheck[] = '.php/login.php';
$paramsToCheck[] = '.php/password_forgotten.php';
$paramsToCheck[] = '.php/sqlpatch.php';
$paramsToCheck[] = 'file_manager.php';
$paramsToCheck[] = 'index.html?';
$paramsToCheck[] = ':2082';
$paramsToCheck[] = ':2083';
$paramsToCheck[] = ':2086';
$paramsToCheck[] = ':2087';

// processing ****************************
/**
 * inoculate against hack attempts which waste CPU cycles
 */
$contaminated = (isset($_FILES['GLOBALS']) || isset($_REQUEST['GLOBALS'])) ? true : false;
$paramsToAvoid  = array('GLOBALS', '_COOKIE', '_ENV', '_FILES', '_GET', '_POST',  '_REQUEST', '_SERVER', '_SESSION', 'HTTP_COOKIE_VARS', 'HTTP_ENV_VARS',  'HTTP_GET_VARS', 'HTTP_POST_VARS', 'HTTP_POST_FILES',  'HTTP_RAW_POST_DATA', 'HTTP_SERVER_VARS', 'HTTP_SESSION_VARS');
$paramsToAvoid[] = 'autoLoadConfig';
$paramsToAvoid[] = 'mosConfig_absolute_path';
$paramsToAvoid[] = 'hash';
$paramsToAvoid[] = 'main';
foreach($paramsToAvoid as $key) {
  if (isset($_GET[$key]) || isset($_POST[$key]) || isset($_COOKIE[$key])) {
    $contaminated = true;
    break;
  }
}
if ($contaminated)
{
  header('HTTP/1.1 406 Not Acceptable');
  exit(0);
}
$requesturi=@$_SERVER['REQUEST_URI'];
$lcrequesturi=strtolower($requesturi);
$query2=$useragent="";
if(isset($_SERVER['QUERY_STRING'])){$query2=@$_SERVER['QUERY_STRING'];}
$query=strtolower($query2);
$querydec2=urldecode($query2); // urldecoded to make signature writing for detection matching easier
$querydec=strtolower($querydec2);
$querydecsws=preg_replace('/\s+/','',$querydec);
$querydecsws=preg_replace("/[^\x9\xA\xD\x20-\x7F]/",'',$querydecsws);
if(isset($_SERVER['HTTP_USER_AGENT'])){$useragent=@$_SERVER['HTTP_USER_AGENT'];}
$lcuseragent=strtolower($useragent);
$lcuseragentsws=preg_replace('/\s+/','',$lcuseragent);
$lcuseragentsws=preg_replace("/[^\x9\xA\xD\x20-\x7F]/",'',$lcuseragentsws);

foreach ($paramsToCheck as $key => $val) {
  if (substr_count($lcrequesturi, $val) || substr_count($query, $val) || substr($query, -1) == '?') {
    $contaminated = TRUE;
  }
}
unset($paramsToCheck, $paramsToAvoid, $key, $val);
if ($contaminated)
{
  header('HTTP/1.1 406 Not Acceptable');
  exit(0);
}
unset($contaminated);
unset($query2,  $query, $querydec2, $querydec, $querydecsws, $useragent, $lcuseragent,  $lcuseragentsws, $requesturi, $lcrequesturi, $lcrequesturisws, $lcpost,  $lcpostsws);
/* *** END OF INOCULATION *** */
```


## Related 

- [Blocking Attacks](/user/troubleshooting/blocking_attacks/)

