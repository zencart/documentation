---
title: Why am I getting 500 INTERNAL SERVER ERROR messages?
description: How do I resolve an HTTP 500 error? 
category: troubleshooting 
weight: 10
---

There are many possible causes of this kind of error, and many of them are completely unrelated to each other.  

Thus, use caution when reviewing the following list. DO NOT go changing permissions willy-nilly "just because" one of these points indicates that that "might" be the cause of the problem. BE SELECTIVE about what you do to try to "fix' the issue.

### A little background:

The server your website is running on, uses a piece of software to do the "serving" of web page content to visitors browsers. THAT server has many rules defined inside it for how things are supposed to work. If *something* goes wrong, it throws up an error, AND it logs that error. 

### MOST IMPORTANT POINT:

The "500 Internal Server Error" is a VERY generic catch-all error that simply means "oops, something went wrong, and I don't know what it was, or at least I'm not going to publicly tell you what it was".  The "500" is the [HTTP response code](/user/troubleshooting/http_response_codes/). 

The actual cause of the error WILL BE LOGGED in the server.  It will NOT be displayed on the screen, since many times the reason might be security-related, and to display the "actual" cause on-screen would tell a hacker exactly what to do next to get around the security systems.  

<font color="#ff0000">THAT is why the fastest way to find the solution to a "500 Internal Server Error" problem is to look at the logs.</font> 

### WHAT ARE THE LOGS? 

There are 2 kinds of logs in this case:  

a) Your site's `/logs/` folder, which stores PHP errors happening in your store. Sometimes a Fatal PHP error will cause your website to trigger a generic 500 Internal Server error. You can find the details of the PHP error in the myDEBUG-xxxxxx.log files in your `/logs/` folder.  

More info is provided in the FAQs on [Zen Cart Debug Logs](/user/troubleshooting/debug_logs/) and 
this [blank page errors](/user/troubleshooting/blank_page/). 

b) Your server's webserver error logs ... ie: Apache/Nginx and maybe PHP itself. Your hosting company will have to give you access to this information if you don't already have an Error Logs menu option in your hosting company's control panel.  

## A word about Windows/IIS hosting

IIS is not recommended.

While Zen Cart has been known to work fine on many Windows/IIS hosting servers, it is primarily tuned best to work with Apache servers, which are more commonly driven by Linux hosts. It has also been frequently demonstrated that if a Zen Cart site is encountering 500 Internal Server Error problems on a Windows host, that moving it to a Linux host quickly removes the problem. This often means that there was something about the Windows Server configuration that was triggering the incompatibility, but no specific pattern describing those unique configuration settings has been identified yet, since the hosting companies haven't been willing to share those details.  

So, switching from Windows/IIS to Linux/Apache is definitely worthy of consideration. It's easier to support and configure on Linux anyway!  

## POSSIBLE CAUSES (in no particular order):

<table width="640" cellspacing="1" cellpadding="1" border="1" align="">

<tbody>

<tr>

<td>Security System  
(mod_security)</td>

<td>mod_security is a security system that runs on the webserver to detect common hacker activity and trip them up if they try to do something rogue. It looks for patterns of commonly-used hacker scripts and words, and if the rule is triggered, it sends a 500 error, and might even lock out the visitor's IP address temporarily.  

The mod_security rule will be listed in the error logs *and* in the mod_security logs.  

See also [errors during product_updates](/user/troubleshooting/product_update_errors/). 
</td>

</tr>

<tr>

<td>suexec</td>

<td>THIS IS BECOMING MORE AND MORE COMMON FOR PCI COMPLIANCE REASONS.  

If the server is configured to use php_suexec (which is intended to provide slightly better security in how files are stored and permissions are managed with PHP scripts), then you're not allowed to set any files or folders to "777" (aka "world-writable) permission levels. The maximum allowed in such cases is typically 755.  

In this situation, if you set a folder to "777", the server throws a 500 Internal Server Error and blocks access to any scripts or files in that folder.  

The blocked folder will be listed in the logs.  

**So, in that case you should use 755 instead of 777 when reading instructions that suggest using "777".**  

</tr>

<tr>

<td>.htaccess syntax errors  

or .htaccess restrictions imposed by the main server configuration</td>

<td>If your server's been configured to restrict you from using certain directives in .htaccess files, but you use something disallowed, then a "500 Internal Server Error" will be triggered, and your site will be inaccessible until you fix the problem.  The exact rule will be recorded in the logs.  
<br /><br />
Further details on .htaccess and server requirements for Zen Cart can be found *inside* the .htaccess files that come *with* Zen Cart.</td>

</tr>

<tr>

<td>PHP errors</td>

<td>

Sometimes when a PHP script encounters an error, either due to a timeout or a syntax problem, or something worse like a logic problem, it *might* trigger a 500 Internal Server Error. It may not always do so, but it may.  

In such cases, if you use the [Zen Cart debug logs](/user/troubleshooting/blank_page/) to review PHP errors, you might discover the cause of the problem there.
</td>

</tr>

<tr>

<td>Missing File</td>

<td>

Using PHP `require` or `require_once` to pull in a file that doesn't exist will generate a 500 error.  For example, attempting to pull in the Magento infrastructure 

```
require_once 'app/Mage.php';
```

doesn't work well in Zen Cart and will cause an HTTP 500 to be returned.
</td>

</tr>

<tr>

<td>Bad configure.php contents</td>

<td>

If the URLs or paths, or anything else for that matter, in your [configure.php files](/user/miscellaneous/configure/) refers to information for a different server, or is not correct for *your* server, then many odd problems may occur, including possibly a 500 error. However, usually it will be very different symptoms. Just be sure that you DO NOT copy your configure.php files from one server to another, even localhost.

</td>

</tr>

<tr>

<td>Wrong email mode</td>

<td>

If your blank-screen or 500-error is occurring at the same time as your store is attempting to send emails, this might be something to look into. Some hosts are extra strict about NOT using the *PHP* setting for [Admin > Configuration > Email](/user/admin_pages/configuration/configuration_email/) in the *Email Transport Protocol* field. 

Instead, set it to *SMTP* and specify the correct email server address in the *SMTP Email Host setting*, also on that screen. For even more assistance on email issues, see [Email Troubleshooting](/user/troubleshooting/email_issues/). 
</td>

</tr>

</tbody>

</table>

