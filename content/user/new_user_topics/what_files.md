---
title: How do I determine which files to edit? 
description: Where do I make the change? 
category: template
weight: 10
---

I want to make changes to the text that shows up in xxxxxxxxx spot on xxxxxx page. How do I find out what where it is, and what file to change?

1. Use a [text-search tool](/user/first_steps/useful_tools/#text-search-tools) that can handle standard text files.  Alternatively, you may use the built-in 
[Developers Toolkit](/user/admin_pages/tools/developers_tool_kit/).  You can enter the words you're looking for right there, and it will find them. 

2. Search everything under the "includes" folder for the text you are trying to change/edit/delete.

3. That will show you the text inside a "define" statement much like this:

```
   define('TEXT_GREET_USER','Welcome to my site');
```

4. This is where you'll be making your changes. You should be sure to save the file according to the Template Overrides 
concept (see the [Overrides Explained FAQ](/user/template/template_overrides/)).

5. Then use this article to be sure you put your CHANGES into the right place:

6. IF YOU ARE desiring to modify the PHP code that "uses" the text you just located, then you need to do another search -- ie: for the `TEXT_GREET_USER` (constant name that you just found), and find the files that reference it. 


