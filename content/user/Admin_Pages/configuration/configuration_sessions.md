---
title: Configuration-Sessions
description: Zen Cart Configuration-Sessions Admin Page 
category: admin_pages
weight: 130
---

<b>Session Directory</b>

<div class='indent'>This should point to the folder specified in your DIR_FS_SQL_CACHE setting in your configure.php files.</div>


<b>Cookie Domain</b>

<div class='indent'>If True the full domain name will be used to store the cookie, e.g. www.mydomain.com. If False only a partial domain name will be used, e.g. mydomain.com. If you are unsure about this, always leave set to true.</div>


<b>Force Cookie Use</b>

<div class='indent'>Force the use of sessions when cookies are only enabled.</div>


<b>Check SSL Session ID</b>

<div class='indent'>Validate the SSL_SESSION_ID on every secure HTTPS page request.</div>


<b>Check User Agent</b>

<div class='indent'>Validate the clients browser user agent on every page request.</div>


<b>Check IP Address</b>

<div class='indent'>Validate the clients IP address on every page request.</div>


<b>Prevent Spider Sessions</b>

<div class='indent'>Prevent known spiders from starting a session.</div>


<b>Recreate Session</b>

<div class='indent'>Recreate the session to generate a new session ID when the customer logs on or creates an account (PHP >=4.1 needed).</div>


<b>IP to Host Conversion Status</b>

<div class='indent'>Convert IP Address to Host Address<br /><br />Note: on some servers this can slow down the initial start of a session or execution of Emails</div>


<b>Use root path for cookie path</b>

<div class='indent'>Normally Zen Cart will use the directory that a store resides in as the cookie path. This can cause problems with some servers. This setting allows you to set the cookie path to the root of the server, rather than the store directory. It should only be used if you have problems with sessions. <strong>Default Value = False</strong><br /><br /><strong>Changing this setting may mean you have problems logging into your admin, you should clear your browser cookies to overcome this.</strong></div>


<b>Add period prefix to cookie domain</b>

<div class='indent'>Normally Zen Cart will add a period prefix to the cookie domain, e.g.  .www.mydomain.com. This can sometimes cause problems with some server configurations. If you are having session problems you may want to try setting this to False. <strong>Default Value = True</strong></div>


