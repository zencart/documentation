---
title: Communication Issues with UPS, PayPal, etc. 
description: Using the utilities in the extras folder to diagnose communication issues 
category: Troubleshooting
weight: 10
---

Zen Cart comes with a folder of utilities called `/extras`. 

> This folder should not be kept on a live site; it should only be present during troubleshooting or debugging.

The following scripts can be run from the `/extras` folder:

- `curltester.php` - Tests cURL communication to some common third party services.   Useful parameters for `curltester.php` are: 
    *   `d=1` or `details=1` -- show CURL connection details -- useful for determining cause of communications problems
    *   `r=1` -- show Response obtained from destination server -- this may contain an error message, but usually means communication was okay
    *   `i=1` -- in conjunction with `d` or `r`, will show the detailed curlinfo certificate data from the host being connected to. Helpful for advanced debugging.

- `ipncheck.php` - Determines if your server is able to connect TO PayPal in order to respond to an incoming IPN notification. (Note: To check whether PayPal can POST and IPN to your store, run a live transaction.) 

    Common symptoms of bad IPN communications:
    - orders not showing up in Zen Cart but PayPal receipt issued when using PayPal IPN module
    - echeck updates not completing when using Express Checkout module

Execution of the scripts can be done by entering the following in your browser's address bar (after uploading the `/extras` folder):  

`https://YOURSITE.com/extras/script-name.php` 

(where `script-name` is the name of one of the scripts above.) 

