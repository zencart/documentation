---
title: Basics - Secure Access 
description: Secure Access to your Zen Cart 
category: first_steps
weight: 10
---

## Having an SSL certificate 

[You need an SSL certificate](/user/first_steps/yes_you_need_ssl/); 
it's part of running an online store. It doesn't matter that you don't do onsite credit card collection; you still need an SSL certificate.

**Don't let this be you!**

![Insecure Cart](/images/insecure_cart.png)

## Secure File Transfer 

**Do not** use plain FTP to access your server's files.  

Although this was a common way to do it back in 2003, it is no longer a good practice, since it is not secure. 

Some secure options are:

- FTPS
- SFTP
- Require explicit FTP over TLS

Availability of these specific options is hoster-dependent but at least one
of them should be available. 

If your hosting company does not offer some mechanism for secure file transfer, then they are most likely not PCI Compliant either, and you should be choosing a different hosting company who takes security seriously.

## Secure access to your Admin

Be sure your `admin/includes/configure.php` file has all URL settings using `https`.  This includes `HTTP_SERVER`, `HTTP_CATALOG_SERVER` and `HTTPS_CATALOG_SERVER`, and if it exists, `HTTPS_SERVER`. 

Use an admin username other than `admin` (or `nimda`).  Make it hard to guess.

## Secure cPanel Access 

Just because you run an SSL on your site doesn't mean your cPanel access is secure.  Look for the padlock in your browser's address bar, and tell your hoster to fix it if it's not there! 

**Don't let this be you!**

![Insecure cPanel](/images/cpanel_insecure.png)

## Secure Passwords 

Make hard to guess!  Passwords like "ABC123" are *not hard to guess* - bad guys will try them.   Use a random combination of letters, numbers and symbols which is at least 8 characters long.  

"But it's hard to remember all these passwords!"  Yes, I know.  That's why there are Password Managers. 

## Use a Password Manager 

Don't rely on your memory or some Post-It notes for password storage.  Use a proper password manager, and use the password generation functions that it has to keep your passwords hard to guess. 

There are many password managers on the market, and many have free tiers; here are a few: 

- [LastPass](https://www.lastpass.com/)
- [1Password](https://1password.com/)
- [Dashlane](https://dashlane.com) 

## Use different passwords for each site

Don't reuse passwords! Now that you have a password manager, allow it to generate and store your passwords so that each one can be unique and hard to guess.  

## Transfer passwords securely

Do not put passwords in an email.  This is not a secure practice.  If you have to send a password to a developer or co-worker, use a more secure means of transmission:

- Over the telephone using the [phonetic alphabet](https://en.wikipedia.org/wiki/NATO_phonetic_alphabet)
- Over SMS 
- One time link generators like [privnote.com](https://privnote.com)


