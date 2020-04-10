---
title: Showing EZ-Page Links 
description: What determines when an EZ-Page link appears? 
category: ezpages
weight: 10
---

We will address the `template responsive_classic` in this article, 
although the information will apply to any properly coded template.

EZ-Page links can be shown without making a code change in three places: 

- Header
- Important Links sidebox
- Footer 

A set of configurations determines where these links are shown.  If you go to
Admin > Tools > EZ-Pages, you will see a set of fields like the following: 

<br />
<img src="/images/ezpages.png" alt="EZ-Pages configuration" />
<br />

- Setting Header = Yes with a sort order > 0 means a link to this page will be displayed by `includes/templates/responsive_classic/templates/tpl_ezpages_bar_header.php`. 

- Setting Sidebox = Yes with a sort order > 0 means a link to this page will be displayed by `includes/modules/sideboxes/ezpages.php`. 

- Setting Footer = Yes with a sort order > 0 means a link to this page will be displayed by `includes/templates/responsive_classic/templates/tpl_ezpages_bar_footer.php`. 

If you do not want the link to appear in any of these places or you are not using these components in your template, you still have the ability to  show an EZ-Page link and have the EZ-Page display properly: 

- use the `Page is Visible` radio button 
- code into the content where you want the link to appear 

If you are already in a PHP block, you'd use: 

```
  echo '<a href="' . zen_href_link(FILENAME_EZPAGES,'page_id') . '">' NEW_PAGE_TITLE . '</a>'; 
```

If you're in HTML (say in a list), you would use 

```
<li><a href="<?php echo zen_href_link(FILENAME_EZPAGES, 'page_id'); ?>"><?php echo NEW_PAGE_TITLE; ?></a></li>

```

where `page_id` is the numeric id of the page as shown on the left hand side of `Admin > Tools > EZ-Pages`, and `NEW_PAGE_TITLE` is a language defined constant for the name of your page.  You would define `NEW_PAGE_TITLE` in a file like, `includes/languages/english/extra_definitions/my_ezpages.php` as follows:

```
<?php 
define('NEW_PAGE_TITLE','Name of My New Page');
```

Once you do this, your link will be displayed and your page content will be displayed when users visit that EZ-Page, by going to `YOURSITE.com/index.php?main_page=page&id=page_id`, even if the page is not displayed in the header, sidebox or footer.  The `visible` flag is a new change in Zen Cart 1.5.6; prior to that, the page had to be set to appear in the header, sidebox or footer. 

