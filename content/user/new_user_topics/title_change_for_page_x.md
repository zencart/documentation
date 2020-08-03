---
title: How do I change the title of main_page=page_X?
description: Changing the name of PAGE_2, PAGE_3 or PAGE_4
category: new_user_topics 
weight: 10
---
To change the name of page_2, page_3 or page_4  

1\. open the appropriate file: `/includes/languages/YOURLANGUAGE/page_?.php`

2\. make the changes to fit your needs  

```
define('NAVBAR_TITLE', 'Page ?');  
define('HEADING_TITLE', 'Page ?');
```

3\. then save the file to:  
`/includes/languages/YOURLANGUAGE/YOURTEMPLATE/page_?.php` and upload to your server.  

**NOTE:** See [Basic Terms](/user/first_steps/basic_terms/) for an 
explanation of `YOURLANGUAGE` and `YOURTEMPLATE` if these terms are 
unfamiliar. 

This technique applies to these pages:

Define | URL
-------|----------
PAGE_2 | index.php?main_page=page_2
PAGE_3 | index.php?main_page=page_3
PAGE_4 | index.php?main_page=page_4

<table>
<tr><td>Define</td><td>URL</td></tr>
<tr><td>PAGE_2</td><td>index.php?main_page=page_2</td></tr>
<tr><td>PAGE_3</td><td>index.php?main_page=page_3</td></tr>
<tr><td>PAGE_4</td><td>index.php?main_page=page_4</td></tr>
</table>
