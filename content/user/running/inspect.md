---
title: Google Chrome Inspect 
description: Using Chrome's tools to keep your site healthy
category: running 
weight: 10 
---

Google Chrome's "Inspect" tool is a tremendous help to anyone creating websites.  

In Google Chrome, right click and select "Inspect." 

![Inspect](/images/browser_inspect.png)

A dialog will come up with a number of options on the top menu bar.
Here are some things to explore: 

- Clicking "Console" will show you reports of any missing or unavailable files (JavaScript, CSS, etc.) 

- Clicking "Lighthouse" will perform a test that will analyze your site speed and whether you are using [outdated JavaScript libraries](/user/upgrading/javascript_updates/)

- Clicking "Elements" will show you the CSS rules that apply to each part of your site, enabling you to try changes right from your browser

Other browsers have similar built-in developer tools; pick your favorite and learn as much as you can about it to keep your site in tip-top shape! 

## Example issues shown in the Console by Inspect 

### Mixed Content 

![Mixed Content](/images/mixed_content.png) 

If you get a mixed content warning, it means something is being loaded over `http` instead of `https`.  In this case, for example, if you check `includes/templates/YOURTEMPLATE/common/html_header.php`, you will see something like 

```
<link href='http://fonts.googleapis.com/css?family=Roboto:400,300,500,700&amp;subset=latin,cyrillic-ext,greek-ext,greek,vietnamese,latin-ext,cyrillic' rel='stylesheet' type='text/css'>

```

just make this load over `https` by changing it to 

```
<link href='https://fonts.googleapis.com/css?family=Roboto:400,300,500,700&amp;subset=latin,cyrillic-ext,greek-ext,greek,vietnamese,latin-ext,cyrillic' rel='stylesheet' type='text/css'>

```


