---
title: Using your logo on packing slips and invoices 
description: Using your logo on packing slips and invoices in Zen Cart 
category: customizing
weight: 10
---

Related: [How do I change the logo in my HTML emails?](/user/email/logo/) 

The logo used on Admin pages and on output from admin is `admin/images/logo.gif`.

If you want to rename this, you should edit the following code from `admin/includes/languages/english.php`

```
// added defines for header alt and text
define('HEADER_ALT_TEXT', 'Admin Powered by Zen Cart :: The Art of E-Commerce');
define('HEADER_LOGO_WIDTH', '200');
define('HEADER_LOGO_HEIGHT', '70');
define('HEADER_LOGO_IMAGE', 'YOURLOGO.png');
```

(The code above assumes your logo is a `png` file.  If your logo is a `jpg` file, the above define would be `YOURLOGO.jpg`, and so forth.) 

Edit the information for your own logo,

Save the file back to `admin/includes/languages/english.php` and upload it to your server.  (Remember there are no overrides in admin.)

Place your logo image in `admin/images/YOURLOGO.png` and upload to your server

If you have changed the size of your logo, please note that the invoice and packing slips functions do not currently take any notice of this. To encourage them to be more receptive, find the following line in `admin/invoice.php` and 
`admin/packingslip.php`.

```
 <td class="pageHeading" align="right"><?php echo zen_image(DIR_WS_IMAGES . HEADER_LOGO_IMAGE, HEADER_ALT_TEXT); ?></td>
```

and edit it to read

```
 <td class="pageHeading" align="right"><?php echo zen_image(DIR_WS_IMAGES . HEADER_LOGO_IMAGE, HEADER_ALT_TEXT, HEADER_LOGO_WIDTH, HEADER_LOGO_HEIGHT); ?></td>
```
