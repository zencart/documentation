---
title: Showing EZ-Page Links 
description: What determines when an EZ-Page link appears? 
category: ezpages
weight: 10
---

We will address the template `responsive_classic` in this article, 
although the information will apply to any properly coded template.

EZ-Page links can be shown without making a code change in three places: 

- Header
- Important Links sidebox
- Footer 

A set of configurations determines where these links are shown.  There is a radio button and sort order for each of the header,
sidebox and footer.  For a page to show up in one of these places, the
associated radio button must be set to *Yes* and the sort order must be greater than 0.
You can see these settings in [Tools > EZ-Pages](/user/admin_pages/tools/ezpages/). 

# Adding a link manually 

In addition to the three places shown above, you can change your
template to show an EZ-Page (say on the product info page) using the technique below.  

The page still needs to be visible, either by 

- enabling one of the three pairs of settings above (header, sidebox or footer), or, 
- Since Zen Cart 1.5.6, using the *Page is Visible* flag. 

Let's suppose the language constant for the 
name of the page is `NEW_PAGE_TITLE` and the EZ-Page id, as shown on 
the left hand side of 
[Tools > EZ-Pages](/user/admin_pages/tools/ezpages/), is 19. 

If you are already in a PHP block, you'd use: 

```
  echo '<a href="' . zen_href_link(FILENAME_EZPAGES,'id=19') . '">' . NEW_PAGE_TITLE . '</a>'; 
```

If you're in HTML (say in a list), you would use 

```
<li><a href="<?php echo zen_href_link(FILENAME_EZPAGES, 'id=19'); ?>"><?php echo NEW_PAGE_TITLE; ?></a></li>
```

or if it's pure HTML (being edited in plain text editor, for example), to do it without PHP would be 

```
<li><a href="index.php?main_page=page&id=19">title-of-ezpage-19</a></li>
```

You would define `NEW_PAGE_TITLE` in a file like, `includes/languages/english/extra_definitions/my_ezpages.php` as follows:

```
<?php 
define('NEW_PAGE_TITLE','Name of My New Page');
```

Once you do this, your link will be displayed and your page content will be displayed when users visit that EZ-Page, by going to `YOURSITE.com/index.php?main_page=page&id=19`, even if the page is not displayed in the header, sidebox or footer.  

The *Page is Visible* flag has been available since Zen Cart 1.5.6; prior to that, the page had to be set to appear in the header, sidebox or footer.  If it were not, users visiting the page would see the message, "Sorry, the page you were attempting to access cannot be found."

See also [creating links to other pages](/user/customizing/creating_links/). 

