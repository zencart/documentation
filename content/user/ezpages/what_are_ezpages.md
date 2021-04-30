---
title: What are EZ-Pages? 
description: The easiest way to add content to your site 
category: ezpages
weight: 1
---
EZ-Pages are a fast, easy way of creating links and additional pages.  

The additional Pages can be for:  

*   New Pages
*   Internal Links
*   External Links

In Addition, there is the ability to create "related" links in the format of a Chapter (group) and its TOC (related pages/links).  

See [Admin Interface to EZ-Pages](/user/admin_pages/tools/ezpages/) to learn about the how EZ-Pages are set up and managed. 


### Link Naming

Links are named by the Page Title. All Links need a Page Title in order to function.  

If you forget to add a Page Title, then you will not be able to add the Link.  

### Enabling/Disabling Links 
There are several ways you may display an EZ-Page link on your site: 

- In your header (by setting Header = Yes and an Order value > 0). 
- In your footer (by setting Footer = Yes and an Order value > 0). 
- In your EZ-Pages sidebox (by setting Sidebox = Yes and an Order value > 0). 


If you don't want the page link in any of those places, you can still 
make the page visible in the storefront by setting the `Page is Visible` radio button.  

### Link Placement

While you have the option of adding Additional Links to the Header, Footer and Sidebox with EZ-Pages, you are not limited to these three Link locations. Links can be in one or more locations simply by enabling the Order for the Location(s) where the Link should appear.

The Link Location Status for the Header, Footer and Sidebox is controlled simply by setting these to Yes or No for each setting. Then, set the Order in which the Link should appear for each location.  

This means that if you were to set Header to Yes 30 and Sidebox to Yes 50 then the link would appear in both the Header and Sidebox in the Order of your Links.  

The Order numbering method is up to you. Numbering using 10, 20, 30, etc. will allow you to sort the Links and add additional Links later.  

Note: a 0 value for the Order will disable the Link from displaying.  

If you do not wish to have the link in any of the three locations, but still
wish to have it available to visitors on your site, simply click the 
Page is Visible <b>Yes</b> radio button. 

### Open in New Window and Secure Pages
With EZ-Pages, each Link can take you to the same, main window for your shop; or, you can have the Link open a brand new New Window. In addition, there is an option for making the Link open as a Secure Page or a Non-Secure Page.  

### Chapter and TOC

The Chapter and TOC, or Table of Contents, are a unique method of building Multiple Links that interact together.  

While these Links still follow the rules of the Header, Footer and Sidebox placement, the difference is that only one of the Links, the Main Link, needs to be displayed anywhere on the site.  

If you had, for example, 5 related Links, you could add the first Link as the Main Link by setting its location to the Header, Footer or Sidebox and set its Order, as usual.  

Next, you need to assign a Chapter or Group number to the Link. This Chapter holds the related Links together.  

Then, set the TOC or Table of Contents setting. This is a secondary Sort Order for within the Chapter.  

Again, you can display any of the Links within a Chapter, as well as making any of these Links the Main Link. Whether the Links all show, or just one or more of the Links show, the Chapter is the key to grouping these Links together in the TOC or Previous/Next.  

**NOTE:** While all Links within a Chapter will display together, you can have the different Links display in the Header, Footer or Sidebox on their own. Or, you can have the additional Links only display when the Main Link or one of the Additional Links within the Chapter has been opened.

The versatility of EZ-Pages will make adding new Links and Pages extremely easy for the beginner as well as the advanced user.  

**NOTE:** HTML editors will often add the opening and closing tags for sections, like `<html>`, `<head>` and `<body>`, to the file you are working on. You may want to remove them, as these are already added to the pages via EZ-Pages.  

The numbering of the Chapters can be done in any manner. But, by number in increments such as 10, 20, 30, etc. you can later insert pages, or links, as needed within the existing pages.  

There is no limit to the number of pages, or links, that can be grouped together using the Chapter.  

The display of the Previous/Next and TOC listing is a setting that can be turned on or off.  

### External Link URL

External Link URLs are links to outside pages not within your shop. These can be to any valid URL such as:  

```
https://www.google.com 
```

You need to include the full URL path to any External Link URL. You may also mark these to open in a New Window or the Same Window.  

### Internal Link URL

Internal Link URLs are links to internal pages within your shop. These can be to any valid URL, but should be written as relative links such as:  

```
index.php?main_page=index&cPath=21  
```

The above Link would take you to the Category for categories_id 21  

While these links can be the Full URL to an Internal Link, it is best to use as a Relative Link, so that if you change domains, or work on a temporary domain or an IP Address, the Link will remain valid.  See [relative URLs](/user/first_steps/relative_urls/) for more information.

Internal Links can also open in a New Window or the Same Window or be for Secure or Non-Secure Pages.  

### EZ-Pages Additional Pages vs Internal Links vs External Links

The Type of Link that you create is based on an order of precedence, where HTML Content will supersede both the Internal Link and the External Link values.  

The External Link URL will supersede the Internal Link URL.  

If you try to set a combination of HTML Content, Internal Link and/or External Link, the Link will be flagged in the listing with a read icon to alert you to your mistake.  

<b>WARNING</b>

When using Editors such as CKEditor, if you hit enter in the HTML Content area,
whitespace will be added. These will be detected as "content" and will override any Internal Link URL or External Link URL.  

### Other options for adding pages 

For many situations, EZ-Pages offer exactly what is needed for creating new pages and new content for your Zen Cart.  However, if you need more flexibility (such as the ability to embed PHP code), take a look at the other options shown in [Adding Pages to my site](/user/customizing/add_pages/). 

