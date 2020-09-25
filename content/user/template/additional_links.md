---
title: How do I add links to the Header and Footer? 
description: Putting important links on every page 
category: template
weight: 10
---

There are two options for adding additional links to the header and footer of your site.

### OPTION 1:

Additional links requires editing two files; `tpl_header.php` and `tpl_footer.php`.
You can add internal page links as well external links. We'll use `tpl_header.php` in this article, but the same procedures would apply to `tpl_footer.php`.

Adding an internal page link (let's use the `Contact Us` page in this example.)

In your text editor, open `includes/templates/YOURTEMPLATE/common/tpl_header.php`. 

Find the following code:

```
<!--bof-navigation display-->
<div id="navMainWrapper">
<div id="navMain">
<ul class="back">
<li><?php echo '<?php echo '<a href="' . HTTP_SERVER . DIR_WS_CATALOG . '">'; ?><?php echo HEADER_TITLE_CATALOG; ?></a></li>
```

Add the following code just below the last line in the above code.

```
<?php if (DEFINE_CONTACT_US_STATUS <= 1) { ?>
    <li><?php echo '<a href="' . zen_href_link(FILENAME_CONTACT_US, '', 'SSL') . '">' . BOX_INFORMATION_CONTACT . '</a>'; ?></li>
<?php } ?>
```

You would add an external link as outlined above.

```
<li><a href="http://external_link.com">External Link Text</a></li>
```

### OPTION 2:

Make sure the EZ-Pages header or footer are activated in [Admin > Configuration > EZ-Pages](/user/admin_pages/configuration/configuration_ezpagessettings/). 

Go to [Admin > Tools > EZ-Pages](/user/admin_pages/tools/ezpages/) and click the `New Page` button.

Fill in the Page Title Box (in our example, add Contact Us)

Select Where you want the link to appear:

```
Header > select Yes and add a Sort Order
Footer > select Yes and add a Sort Order
```

![EZ-Pages header and footer](/images/ezpages_header_footer.png)

Scroll down to the `Internal Link URL` box

Add your link as follows - `index.php?main_page=contact_us` 

![EZ-Pages internal link](/images/ezpages_internal_link.png)

(You would follow this procedure for whatever page you are adding)

