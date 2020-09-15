---
title: Why am I getting 500 or 406 or 404 or 403 errors during product updates?
description: Product Update returns HTTP status 500, 406, 404 or 403
category: troubleshooting 
weight: 10
---

**Symptom:**

When updating product details (or EZ-Pages content and other areas), when certain keywords are used in the content, an error message similar to the following may appear:

```
Forbidden - You don't have permission to access /admin/product.php on this server.
```

You also may see this message: 

```
Additionally, a 404 Not Found error was encountered while trying to use an ErrorDocument to handle the request.
```

Sometimes the error may appear as a `500 Internal Server Error` or `406` error.

**Cause:**

Many servers nowadays use a tool in their Apache Webserver software configuration called "mod_security" in order to prevent against hack attempts on the server.  This tool monitors the content of words/data submitted in forms on web pages, and if certain keywords are found, it flags the entire form-submission as at-risk, and prevents the entered data from being saved.

Common keywords which may get flagged include: `INSERT` or `UPDATE` and other commonly-used SQL commands. 

The numbers 500, 406, 404 or 403 are 
the [HTTP response code](/user/troubleshooting/http_response_codes/). 

### Possible Solutions:
1. Don't use any words which are restricted by your host's rules.

2. Get your host to change or relax the mod_security rules.

3. You can try disabling mod_security for your admin area by putting this in your `/admin/.htaccess` file:

```
SecFilterInheritance Off
```

or this:

```
SecFilterScanPOST Off
```

If that doesn't work, you'll need to talk to your hosting company for specific assistance about ways in which *they* will allow you to override mod_security filters in your admin area.

