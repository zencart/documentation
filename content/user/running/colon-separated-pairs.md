---
title: Colon Separated Pair configuration 
description: Specifying configuration values using colon-separated pairs in Zen Cart 
category: Running
weight: 10
---

Frequently a configuration setting will require several pieces of input - for example, the Table Rate shipping configuration.  

To express the configuration "for up to 2 pounds, charge $5, but for over 2 pounds but under 7 pounds, charge $10," the following string is used:

<pre>
2:5,7:10 
</pre>

This could also express the configuration "1-2 items, charge $5, 3-7 items, charge $10."  How the figures are interpreted depends on the context in which they are used.  

This pattern of configuration, called "colon-separated pairs" is used in a number of places in Zen Cart. 

