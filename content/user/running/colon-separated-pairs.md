---
title: Colon Separated Pair configuration 
description: Specifying configuration values using colon-separated pairs in Zen Cart 
category: Running
weight: 10
---

Frequently a configuration setting will require several pieces of input - for example, the Table Rate shipping configuration.  To express the configuration "charge $5 for up to 2 pounds, but $10 for 2.01 pounds to 7 pounds," the following string is used:

<pre>
2:5,7:10 
</pre>

This could also express the configuration "1-2 items, charge $5, 3-7 items, charge $10." 

This pattern of configuration, called "colon-separated pairs" is used in a number of places in Zen Cart. 

