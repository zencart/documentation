---
title: Why plugins? 
description: Why does Zen Cart use plugins? 
category: plugins
weight: 10
---

"Why isn't plugin *X* part of the Zen Cart core?" is a question that comes up frequently.  
Although the reasons are complicated and varied, here are some common explanations: 

## The functionality is not universally needed 
Although a specific modification may seem vital to you, many people are successfully running 
online stores without it.  Such a modification would be rejected for inclusion into the core for that reason. 

## The functionality is OS dependent 
A plugin like [Backup MySQL](https://www.zen-cart.com/downloads.php?do=file&id=7) requires extensive logic to check various OS-specific settings. 
This is difficult to maintain and subject to change outside the release schedule for Zen Cart,
so it's not a candidate for inclusion into the core. 
Similar logic applies to URL rewriting plugins, which are often tied to a particular web server such as Apache. 

## The plugin is an integration with an external system 

As an example, consider the USPS shipping module. 

The USPS shipping module is not bundled with Zen Cart because it changes on a schedule set by USPS, not Zen Cart.
Thus, any particular release of Zen Cart which included USPS could be shipping an obsolete version of the software. 

For this reason, USPS functionality is provided by a plugin. 

The same is true for many other shipping and payment modules. 

## Desire to keep the core small 
The smaller Zen Cart is, the easier it is to maintain, for both the developers on the core team and for individual store owners.  
For this reason, even very powerful and popular plugins are often rejected for inclusion into the core. 


