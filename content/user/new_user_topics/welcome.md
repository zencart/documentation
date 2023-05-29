---
title: How do I change the "Welcome Guest" message?
description: Removing or changing the message for non-logged-in users 
category: new_user_topics 
weight: 10 
---

If you want to replace this message with one of your own, you must
override the language file for the `index.php` page. 

## 1.5.8 and above 
Edit `includes/languages/english/YOURTEMPLATE/lang.index.php`. 
(Copy the file 
`includes/languages/english/lang.index.php` to 
`includes/languages/english/YOURTEMPLATE/lang.index.php` if the override file doesn't already exist.)

Locate these lines of code:

```
    'TEXT_GREETING_GUEST' => 'Welcome <span class="greetUser">Guest!</span> Would you like to <a href="%s">log yourself in</a>?',
    'TEXT_GREETING_GUEST_SHOWCASE' => 'Welcome, please enjoy our online showcase.',
    'TEXT_GREETING_PERSONAL' => 'Hello <span class="greetUser">%s</span>! Would you like to see our <a href="%s">newest additions</a>?',
```

As you can see, there are two Welcome messages depending upon whether you wish Zen Cart to be a fully functioning store, or just a showroom.

Edit the message starting from the word “Welcome” but be careful not to change the text in angled brackets, or the brackets themselves. Make sure that the single quote marks are not left out. If you want to include an apostrophe in your text e.g. “Lucy's Store”, you will need to put an escape character before the apostrophe, i.e. 

```
Lucy\'s Store
```

## 1.5.7 and below 
Edit `includes/languages/english/YOURTEMPLATE/index.php`. 
(Copy the file 
`includes/languages/english/index.php` to 
`includes/languages/english/YOURTEMPLATE/index.php` if the override file doesn't already exist.)

Locate these lines of code:

```
if (STORE_STATUS == '0') {
   define('TEXT_GREETING_GUEST', 'Welcome <span class="greetUser">Guest!</span> Would you like to <a href="%s">log yourself in</a>?');
} else {
   define('TEXT_GREETING_GUEST', 'Welcome, please enjoy our online showcase.');
}
define('TEXT_GREETING_PERSONAL', 'Hello <span class="greetUser">%s</span>!');
```

As you can see, there are two Welcome messages depending upon whether you wish Zen Cart to be a fully functioning store, or just a showroom.

Edit the message starting from the word “Welcome” but be careful not to change the text in angled brackets, or the brackets themselves. Make sure that the single quote marks are not left out. If you want to include an apostrophe in your text e.g. “Lucy's Store”, you will need to put an escape character before the apostrophe, i.e. 

```
Lucy\'s Store
```

## Eliminating the Welcome Message 
If you want to eliminate “Welcome Guest! Would you like to log yourself in?” message completely, turn off the Customer Greeting in your 
[Admin > Configuration > Layout settings](/user/admin_pages/configuration/configuration_layoutsettings/).  Go to *Customer Greeting - Show on Index Page* and set it to 0.

NOTE:  Completely removing this message will result in an Accessibility structure violation as the result would be h1 to h3 on the main page versus h1 (Congratulations!), h2 (Welcome), and h3 (define_main_page.php).

