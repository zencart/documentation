---
title: How do I enable SSL after I have installed Zen Cart?
category: installing
weight: 1
---
SSL (secure socket layer) is used to encrypt communications between the browser and the server, thus protecting sensitive data being transferred from your customers to your store. You will recognize SSL mode by seeing the familiar HTTPS:// in the URL in your browser's address bar. This should always also be accompanied by a secure padlock symbol in your browser, often in the status bar at the bottom of the browser window or in the address bar.  

Considerations:  

# 1\. Determine what kind of SSL service you have

You will need to arrange with your hosting company to have SSL capability added to your hosting account. There are two forms of SSL service: dedicated and shared.  

**<u>Dedicated SSL</u>**  
- URL looks like: [https://www.your_site.com](https://www.your_site.com)  
- requires purchase of an SSL certificate, at an annual fee ranging from $20 to $900 per year (you do NOT need the most expensive one for simple secure SSL use on your site. From a technical perspective, a low cost certificate is just as secure as the more expensive one). The certificate is usually installed by your hosting company. You can purchase one yourself or have your hosting company purchase it for you.  
- usually requires a small monthly fee increase to your hosting account for a "dedicated IP address". Confirm with your hosting company.  
- when you purchase the certificate, decide FIRST whether you want your SSL URL to include the "[www."](http://www.%22) prefix or not. Ideally ask the certificate company to allow you to use BOTH. They can do that, usually at no extra charge.  
- Dedicated SSL is a much better shopping experience for your customers, and also more likely to be easier to configure for your store to use than a Shared Certificate.  

<u>**Shared SSL**</u>  
- Recommended only for testing and development. Live stores should ideally use a Dedicated SSL certificate.  
- This is a certificate that's been purchased by your hosting company, and you merely share its use. Often the hosting company allows you to use it for free.  
- Less friendly experience for your customers because the URL looks nothing like your store's URL. May also be problematic for some stores depending on server configuration and impact on session handling.  
- URL could have many forms:  
-- [https://your_host.com/~your_username/](https://your_host.com/~your_username/)  
-- [https://your_host.com/your_username/](https://your_host.com/your_username/)  
-- [https://your_username.your_host.com/](https://your_username.your_host.com/)  
-- and various other formats  
- There is usually no special setup required in your hosting account. You simply need to ask your hosting company for the correct URL to use.  

**IMPORTANT NOTE ABOUT SSL AND ZEN CART:  
**- It is important that your hosting company's servers be configured to serve both SSL and non-SSL content from the SAME folder on the SAME server. Attempting to use a hosting service whose SSL service is on a separate server or points to a separate folder will result in numerous operational problems, and possibly very complicated maintenance problems.  
- The hosting company should allow the $_SERVER variable values to be set via traditional means (ie: 'SSL=on' or 'SERVER_PORT=443' or 'HTTPS=1', etc). If they can't do that, then Zen Cart may have challenges switching into SSL mode automatically. Most good reputable hosting companies already do this. Those who don't should generally be avoided.

# 2\. Make sure SSL is working on your hosting account first

FIRST, make sure you've got SSL enabled on your hosting account. Work with your hosting company to get a certificate installed and to purchase one if necessary. As mentioned above, IT IS RECOMMENDED THAT YOU REGISTER IT TO YOUR "[www."](http://www.%22) address, such as [www.your_site.com](http://www.your_site.com) (and not just "your_site.com"), or alias it to both URL forms.  
Can you get to "[https://www.your_site.com"](https://www.your_site.com%22) ? If not, ask your hosting company how to do it.  
If you can't access your site using an HTTPS:// address, don't try to enable SSL in Zen Cart or you'll just end up with broken pages in your store!!! **Get the SSL working first before you enable it in your store.**  

# 3\. Enable SSL support in Zen Cart

Once you've had your hosting company install your SSL certificate, **and you have confirmed that going to "[https://www.your_site.com"](https://www.your_site.com%22) actually works without an error**, you can turn on SSL support in Zen Cart using the following information:  
You will need to make changes in both the /includes/configure.php and /your_renamed_admin/includes/configure.php.  
Change **includes/configure.php** and **admin/includes/configure.php** to:  

<pre>
// Define the webserver and path parameters  
define('HTTP_SERVER', 'http://www.YOUR_STORE.com');  
define('HTTPS_SERVER', 'https://www.YOURSTOP.com](https://www.YOURSTORE.com)');  
define('ENABLE_SSL', 'true');  
</pre>

NOTE: (in your admin configure.php, the above define is called `ENABLE_SSL_CATALOG`)  

If you're using a shared SSL certificate, then on the HTTPS_SERVER line use the URL for that certificate, as provided by your hosting company.  

If you want your ENTIRE site to be served over SSL, then use https on both defines:  

<pre>
define('HTTP_SERVER', 'https://www.YOURSTORE.com');  
define('HTTPS_SERVER', 'https://www.YOURSTORE.com](https://www.YOURSTORE.com)');  
define('ENABLE_SSL', 'true');  
</pre>

**ADMIN SECURITY NOTE:** In Zen Cart v1.x, if you want to secure all your ADMIN pages with SSL, set the HTTP_SERVER in your "/admin/includes/configure.php" to the same working URL as your HTTPS_SERVER setting. (You will then have both an HTTP_SERVER and HTTPS_SERVER defined to the same value.) (Also, if your DIR_WS_ADMIN looks something like '/adminfoldername/' and doesn't have references to $p1 or any other $ variables in it, then do the same with DIR_WS_ADMIN to make it match DIR_WS_HTTPS_ADMIN.) **THIS IS REQUIRED FOR PCI COMPLIANCE, and will happen automatically with new installations of v1.5.x and newer.**  

**IMPORTANT NOTE:** _Remember, your configure.php files are probably marked read-only. You'll need to change them to read-write in order to upload your updates, and then put them back to read-only._ [See the FAQ on setting file permissions.](https://docs.zen-cart.com/user/installing/permissions/)

If you are intending to make ALL your pages be SSL, then set HTTP_SERVER to an https URL.  

# 4\. <font color="#FF0000">Clear your browser's cache and cookies</font>

After making these changes, if you don't clear your browser's cache and cookies, it's possible that your logins will not work because the browser is remembering information from the old URL. A simple clearing of the cache and cookies, and sometimes a restart of the browser application, is all it takes.  

**<u>Advanced information:</u>**  
The URLs are built by combining settings, like this:  

Storefront:  
http: HTTP_SERVER + DIR_WS_CATALOG  
https: HTTPS_SERVER + DIR_WS_HTTPS_CATALOG  

Admin:  
http: HTTP_SERVER + DIR_WS_ADMIN  
https: HTTPS_SERVER + DIR_WS_HTTPS_ADMIN  

So, it's usually a simple matter of setting HTTPS_SERVER to the https URL of your domain.  
With shared SSL, it can be slightly more complicated because there are about 5 different ways that a shared SSL URL can be formed. In such cases, treat DIR_WS_HTTPS_ADMIN as the "/store-foldername/my-admin-foldername/" and the rest of the URL goes into the HTTPS_SERVER setting, such as: [https://shared-servername.com/~hostingaccountname](https://shared-servername.com/~hostingaccountname) or [https://shared-servername.com/websitename.com](https://shared-servername.com/websitename.com) etc. That way the DIR_WS_xxxx value is ONLY the value of the path from the public_html folder onward.  

And yes, if you've got SSL active on your site, then in your admin you should make your HTTP_SERVER and DIR_WS_ADMIN be the same as your HTTPS_SERVER and DIR_WS_HTTPS_ADMIN
