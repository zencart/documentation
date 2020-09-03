---
title: How do I change the "Welcome Guest" message?
description: Removing or changing the message for non-logged-in users 
category: new_user_topics 
weight: 10 
---

If you want to eliminate “Welcome Guest! Would you like to log yourself in?” message completely, turn off the Customer Greeting in your 
[Admin > Configuration > Layout settings](/user/admin_pages/configuration/configuration_layoutsettings/).  Go to *Customer Greeting - Show on Index Page* and set it to 0.

If you want to replace this message with one of your own, 
edit the file 
`includes/languages/english/YOURTEMPLATE/index.php`, 
and locate these lines of code:

```
if (STORE_STATUS == '0') {
   define('TEXT_GREETING_GUEST', 'Welcome <span class="greetUser">Guest!</span> Would you like to <a href="%s">log yourself in</a>?');
} else {
   define('TEXT_GREETING_GUEST', 'Welcome, please enjoy our online showcase.');
}
define('TEXT_GREETING_PERSONAL', 'Hello <span class="greetUser">%s</span>!');
```

As you can see, there are two Welcome messages depending upon whether you wish Zen Cart to be a fully functioning store, or just a showroom.

Edit the message starting from the word “Welcome” but be careful not to change the text in angled brackets, or the brackets themselves. Make sure that the single quote marks are not left out. If you want to include an apostrophe in your text e.g. “Lucy's Store”, you will need to put an escape character before the apostrophe, i.e. “Lucy\'s Store”.

Save the edited file and upload it to your server.

