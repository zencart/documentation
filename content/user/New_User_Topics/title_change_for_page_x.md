---
title: How do I change the title of main_page=page_X?
category: new_user_topics 
weight: 1
---
To change the name of page_2, page_3 or page_4  

1\. open the appropriate file: `/includes/languages/ENGLISH/page_?.php`

2\. make the changes to fit your needs  

```
define('NAVBAR_TITLE', 'Page ?');  
define('HEADING_TITLE', 'Page ?');
```

3\. then save the file to:  
`/includes/languages/ENGLISH/YOURTEMPLATE/page_?.php` and upload to your server.  

NOTE: **CAPITALIZED** words refer to a folder or language that you choose. We use **YOURTEMPLATE** for your template and **ENGLISH** for your language by default. These generic terms should be changed to  the name of the  template/language you are using.
