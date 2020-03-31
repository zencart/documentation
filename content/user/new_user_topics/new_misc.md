---
title: Miscellaneous Questions from New Zen Cart Users 
description: Things New Zen Cart Users Need to Know 
category: new_user_topics 
weight: -1 
---

{{< misc >}} 

--- 

### How do I change the "Welcome Guest" message?

If you want to eliminate “Welcome Guest! Would you like to log yourself in?” message completely, turn off the Customer Greeting in your 
[Admin -> Configuration -> Layout settings](/user/admin_pages/configuration/configuration_layoutsettings/).  Go to *Customer Greeting - Show on Index Page* and set it to 0.

If you want to replace this message with one of your own, 
edit the file 
`includes/languages/english/YOURTEMPLATE/index.php`, 
and locate these lines of code:

```
if (STORE_STATUS == '0') {>>
   define('TEXT_GREETING_GUEST', 'Welcome <span class="greetUser">Guest!</span> Would you like to <a href="%s">log yourself in</a>?');
} else {
   define('TEXT_GREETING_GUEST', 'Welcome, please enjoy our online showcase.');>>
}
define('TEXT_GREETING_PERSONAL', 'Hello <span class="greetUser">%s</span>!');
```

As you can see, there are two Welcome messages depending upon whether you wish  Zen Cart to be a fully functioning store, or just a showroom.

Edit the message starting from the word “Welcome” but be careful not to change the text in angled brackets, or the brackets themselves. Make sure that the single quote marks are not left out. If you want to include an apostrophe in your text e.g. “Lucy's Store”, you will need to put an escape character before the apostrophe, i.e. “Lucy\'s Store”.

Save the edited file and upload it to your server.

---

### How do I change the "Congratulations! you have successfully installed..." Message?


If you want to change `Congratulations! You have successfully installed your Zen Cart®; E-Commerce Solution` with your own text, do the following:

Open the `includes/languages/english/index.php` file and find the following code:

```
  define('HEADING_TITLE', 'Congratulations! You have successfully installed your Zen Cart&reg; E-Commerce Solution.');
```

Replace the text starting “Congratulations” with your own text. Make sure that the single quote marks are not left out.

This line occurs twice, so be sure to replace both lines. 

Save the edited file to `includes/languages/english/YOURTEMPLATE/index.php` and upload it to your server.

---

### How do I change the "Sales Message Goes Here" or "Tagline Here" text?

To change the `Sales Message Goes Here` or `Tagline Here` text to say what you want, do the following: 

Open `includes/languages/english/header.php` in your text editor. Find the following line of code:

```
define('HEADER_SALES_TEXT', 'Tagline Here');
```

Replace `Tagline Here` with your own text, making sure that the single quote marks are not left out.

Save the edited file to `includes/languages/english/YOURTEMPLATE/header.php` and upload it to your server.

NB: By default, the text “Sales Message Goes Here” is also located in `includes/languages/english/header.php` 

```
define('HEADER_SALES_TEXT', 'Sales Message Goes Here');
```

Recommended additional reading:
[How do I set up the template overrides?](/user/new_user_topics/overrides)

---

### How do I turn off the listing of categories that goes across the top of my page?

These are called the *Category Tabs*, and can be switched off by going to [Admin -> Configuration -> Layout Settings](/user/admin_pages/configuration/configuration_layoutsettings/) and setting *Categories-Tabs Menu ON/OFF* to zero.

---

### How do I remove the word "Home" in the middle column?

On some pages, to the right of the categories sidebox, the word "Home" (or perhaps "Home > some-category-name") appears above the page content. 

These are called the *breadcrumbs* (think Hansel and Gretel).  They show where you are and how to get back to previous locations. You can either turn them off completely or you can turn themoff only on the main page. Although breadcrumbs may look a little odd on your home page, they can very useful to your users as they go deeper into your site.  

To turn them off, go to [Admin -> Configuration -> Layout settings](/user/admin_pages/configuration/configuration_layoutsettings/) and set *Define Breadcrumb Status* to 0. 


---
<!-- please keep this at the end --> 
{{< faq_questions >}}
