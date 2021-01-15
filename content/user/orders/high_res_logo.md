---
title: Can I print a high resolution logo on my invoices and packing slips?
description: Branding your invoices and packing slips
category: orders
weight: 10
aliases: 
    - /user/customizing/use_company_logo/
---

You can. Firstly, if you don't already have it, create your high resolution logo at the size and resolution that you would like to print it. Then upload it to the `admin/images` folder.

If it's called something other than `logo.gif`, edit the following block in the `admin/includes/languages/english.php` file

```
// added defines for header alt and text
define('HEADER_ALT_TEXT', 'Admin Powered by Zen Cart :: The Art of E-Commerce');
define('HEADER_LOGO_IMAGE', 'logo.gif');
define('HEADER_LOGO_WIDTH', '200px');
define('HEADER_LOGO_HEIGHT', '70px');
```

Within this block, your should also set appropriate width and height settings for display - they will be used for the logo that appears at the top of all your Admin pages. However, they will not be used for the pages where you generate invoices or packing slips. We'll manage that by adding the following to your `admin/includes/stylesheet.css`

```
.pageHeading img {width:200px; height:70px}

@media print {
    .pageHeading img {width:4in; height:1.4in}
}
```

The first line dictates the size you want the logo to appear on the invoices and packingslips screen, and the block of three lines that follows it determines the physical size that you want it to print at. This would ideally be the actual size that created and saved your logo. I've defined this in images, but if your browser supports it you can equally well use cm, mm, em, ex, % and even for very serious designers pc (picas).

Finally,  to prevent your big new image from blowing up all your Admin pages find the following code in your `admin/includes/header.php` file

```
zen_image(DIR_WS_IMAGES . HEADER_LOGO_IMAGE, HEADER_ALT_TEXT); 
```

and replace it with

```
zen_image(DIR_WS_IMAGES . HEADER_LOGO_IMAGE, HEADER_ALT_TEXT, HEADER_LOGO_WIDTH, HEADER_LOGO_HEIGHT);
```

## Related Articles 
- [How do I change the logo in my HTML emails?](/user/email/logo/) 
- [Changing the logo in the header](/user/new_user_topics/change_header_logo/)


