---
title: Introduction
weight: 1
---

`zcgo` is a command line interface for Zen Cart that allows developer to run certain actions.

It is somewhat like the `artisan` command for `Laravel`

Currently those actions are centered around the new array style language files, but it's 
hoped in the future to allow for other commands, such as creating/updating databases without running a full installer
 etc.

`zcgo` relies on `composer` to provide namespacing to access certain classes. So in order to use `zcgo` 
you need to do a `composer update` 

In fact it's better if you do 
`composer dump-autoload` followed by `composer update`

