---
title: EZ-Pages
category: admin_pages
weight: 10
---
This page allows you to add and remove special EZ-Pages, pages which are easier to create or edit than standard PHP or HTML.

<img src="/images/ezpages_listing.png" alt="EZ-Pages list" />

The number on the left hand side is the EZ-Page id.

# Adding New EZ-Pages 

At the bottom right side of the page shown above is a "New Page" button.  Press it, and you'll be taken to a page creation screen. 

# Modifying and Deleting EZ-Pages 

If you select a specific EZ-Page, a sidebar appears with Edit and Delete buttons. 


# Setting Visibility 

A set of configurations determines where links to EZ-Pages are shown. In  Admin > Tools > EZ-Pages, you will see a set of fields like the following: 

<br />
<img src="/images/ezpages.png" alt="EZ-Pages configuration" />
<br />

- Setting Header = Yes with a sort order > 0 means a link to this page will be displayed by `includes/templates/responsive_classic/templates/tpl_ezpages_bar_header.php`. 

- Setting Sidebox = Yes with a sort order > 0 means a link to this page will be displayed by `includes/modules/sideboxes/ezpages.php`. 

- Setting Footer = Yes with a sort order > 0 means a link to this page will be displayed by `includes/templates/responsive_classic/templates/tpl_ezpages_bar_footer.php`. 

If you do not want the link to appear in the header, footer or sidebox, or you are not using these components in your template, you still have the ability to  show an EZ-Page link and have the EZ-Page display properly: 

- use the `Page is Visible` radio button 
- Update the template where you want the link to appear. See [building a link to an EZ-Page](/user/ezpages/ezpages_display/).  

# Using TOC

With EZ-Pages you can build stand-alone pages or you can build a set of 
related pages which are connected by a table of contents.

(i) When using TOC, make sure to mark all pages in a collection with TOC=yes, not just the main page.

(ii) Give all pages in the same collection the same Chapter number.


For more information, see the [EZ-Page FAQs](/user/ezpages/). 
