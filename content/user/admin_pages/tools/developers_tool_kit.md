---
title: Developer's Tool Kit 
category: admin_pages
weight: 10
---

The Developers Tool Kit is an essential tool for anyone involved in customizing Zen Cart.

The Developers Tool Kit will search through all the files and directories under the directory where you installed Zen Cart for an exact match with the entered text. (Related article: [Finding Which Files To Edit](/user/new_user_topics/what_files/)

You can use text editors and other tools directly on your PC to search through files as well.

With the Developers Tool Kit, you can filter your searches to:

- Language files
- Function files
- Class files
- Template files
- All files

Most of the time, searching through **All Files** will give the best and most reliable result. 

You can also search through Configuration Settings, and even do quick edits to configuration values.


### Searching for text
Most text is stored in the language files, but there are a few exceptions where text is stored in the database. If you want to change some text from somewhere, just enter the text you want to modify in the input box labeled "Look-up in all files" in the Developers Tool Kit, then select the option from the drop-down menu labeled "All Files Look-ups:" and hit the search button.

If you get too many results, try to narrow it down by specifying more text to search for if possible. If you get too few results, try to increase the results by specifying less text to search for. Keep in mind that text may actually be sequenced into multiple parts as code, and html tags may also be included somewhere in the text. This means that searching for just a small part of the text, as in a few words rather than the full sentence, is sometimes necessary because the search term must be an exact match.


E.g. searching for "sales message here" does not match "sales message goes here", so search for "sales message" instead.

