---
title: Character Sets 
description: Representing characters outside US ASCII
category: upgrading 
weight: 10
---

A character set is a set of codes which represent a written language.  For example, the latin1 character set can represent 256 unique characters, which is sufficient for written English.  

As people began to Internationalize computer user interfaces, it was realized that larger character sets were required.  The current standard character set (used by the current version of Zen Cart) is called UTF8MB4. 

When you try to display a character using a character set that cannot represent it, often the result will look like this: 

 � 

Seeing this symbol indicates that you may not be using UTF8MB4 throughout your cart.  Things to check are: 

- The `DB_CHARSET` value in your [configure.php](/user/miscellaneous/configure/) file.  This setting is the encoding between your database and the output of pages on your site.
- The `CHARSET` value in your language files in `includes/languages/YOURTEMPLATE/`.  For example, if your template is bootstrap and your store uses English and French, check both `includes/languages/bootstrap/english.php` and `includes/languages/bootstrap/french.php`.  This setting controls the `<meta charset="YOURENCODING">` tag at the top of your web pages. 
- Your database tables.  If you have not yet gone through the process of [converting from iso-8859-1 to utf8](/user/upgrading/convert_to_utf8/), you may need to. 

You may also need to check: 
- The `$locales` value in your language files in `includes/languages/YOURTEMPLATE/`.  

### Related Articles

- [Converting from iso-8859-1 to utf8](/user/upgrading/convert_to_utf8/) 
- [Character Set](/user/upgrading/detailed_upgrading/#character-set)

