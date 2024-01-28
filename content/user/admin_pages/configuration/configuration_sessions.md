---
title: Configuration ≫ Sessions
category: admin_pages
weight: 130 
---

<h2 id="session_directory">Session Directory</h2>

<div class='indent'>Key: <b>SESSION_WRITE_DIRECTORY</b><br />
Path: <b>Configuration > Sessions</b><br />
Description: This should point to the folder specified in your DIR_FS_SQL_CACHE setting in your configure.php files.</div>


<h2 id="cookie_domain">Cookie Domain</h2>

<div class='indent'>Key: <b>SESSION_USE_FQDN</b><br />
Path: <b>Configuration > Sessions</b><br />
Description: If True the full domain name will be used to store the cookie, e.g. www.mydomain.com. If False only a partial domain name will be used, e.g. mydomain.com. If you are unsure about this, always leave set to true.</div>


<h2 id="force_cookie_use">Force Cookie Use</h2>

<div class='indent'>Key: <b>SESSION_FORCE_COOKIE_USE</b><br />
Path: <b>Configuration > Sessions</b><br />
Description: Force the use of sessions when cookies are only enabled.</div>


<h2 id="check_ssl_session_id">Check SSL Session ID</h2>

<div class='indent'>Key: <b>SESSION_CHECK_SSL_SESSION_ID</b><br />
Path: <b>Configuration > Sessions</b><br />
Description: Validate the SSL_SESSION_ID on every secure HTTPS page request.</div>


<h2 id="check_user_agent">Check User Agent</h2>

<div class='indent'>Key: <b>SESSION_CHECK_USER_AGENT</b><br />
Path: <b>Configuration > Sessions</b><br />
Description: Validate the clients browser user agent on every page request.</div>


<h2 id="check_ip_address">Check IP Address</h2>

<div class='indent'>Key: <b>SESSION_CHECK_IP_ADDRESS</b><br />
Path: <b>Configuration > Sessions</b><br />
Description: Validate the clients IP address on every page request.</div>


<h2 id="prevent_spider_sessions">Prevent Spider Sessions</h2>

<div class='indent'>Key: <b>SESSION_BLOCK_SPIDERS</b><br />
Path: <b>Configuration > Sessions</b><br />
Description: Prevent known spiders from starting a session.</div>


<h2 id="recreate_session">Recreate Session</h2>

<div class='indent'>Key: <b>SESSION_RECREATE</b><br />
Path: <b>Configuration > Sessions</b><br />
Description: Recreate the session to generate a new session ID when the customer logs on or creates an account (PHP >=4.1 needed).</div>


<h2 id="ip_to_host_conversion_status">IP to Host Conversion Status</h2>

<div class='indent'>Key: <b>SESSION_IP_TO_HOST_ADDRESS</b><br />
Path: <b>Configuration > Sessions</b><br />
Description: Convert IP Address to Host Address<br /><br />Note: on some servers this can slow down the initial start of a session or execution of Emails</div>


<h2 id="use_root_path_for_cookie_path">Use root path for cookie path</h2>

<div class='indent'>Key: <b>SESSION_USE_ROOT_COOKIE_PATH</b><br />
Path: <b>Configuration > Sessions</b><br />
Description: Normally Zen Cart will use the directory that a store resides in as the cookie path. This can cause problems with some servers. This setting allows you to set the cookie path to the root of the server, rather than the store directory. It should only be used if you have problems with sessions. <strong>Default Value = False</strong><br><br><strong>Changing this setting may mean you have problems logging into your admin, you should clear your browser cookies to overcome this.</strong></div>


<h2 id="add_period_prefix_to_cookie_domain">Add period prefix to cookie domain</h2>

<div class='indent'>Key: <b>SESSION_ADD_PERIOD_PREFIX</b><br />
Path: <b>Configuration > Sessions</b><br />
Description: Normally Zen Cart will add a period prefix to the cookie domain, e.g.  .www.mydomain.com. This can sometimes cause problems with some server configurations. If you are having session problems you may want to try setting this to False. <strong>Default Value = True</strong></div>


