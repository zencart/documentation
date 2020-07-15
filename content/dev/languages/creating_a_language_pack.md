---
title: Creating a New Translation
description: Creating a New Translation Pack for Zen Cart 
weight: 100 
layout: docs
---
To create a new language pack you should start by copying all the english files to your new language directory sturcture.  
- Copy `includes/languages/english.php` to `includes/languages/YOURLANGUAGE.php`  
- Copy `includes/languages/english/` and all sub directories to `includes/languages/YOURLANGUAGE/`  
- Copy `admin/includes/languages/english.php` to `admin/includes/languages/YOURLANGUAGE.php`  
- Copy `admin/includes/languages/english/` and all sub directories to `admin/includes/languages/YOURLANGUAGE/`  

if you are not using css buttons then you will also need to create  
- `includes/templates/template_default/buttons/YOURLANGUAGE/` and 
- `includes/templates/responsive_classic/buttons/YOURLANGUAGE/` then fill with images of the buttons in your language  

Ideally you should also create 
- `emails` and modify the email template files from english to your language

Finally if you wish to do a complete job you will need to update the description held in the configuration table. These effect the admin area only. You can create a sql file to update these.

so if you are creating a Welsh language pack, using cymraeg for the name, you would have a directory structure like this
- emails  
    - email_common.css  
    - email_template_checkout.htm  
    - more html files  
- admin  
    - includes  
        - languages  
            - cymraeg.php  
            - cymraeg  
               - admin_account.php  
               - more php files  
               - extra_definitions  
                   - ckeditor.php  
                   - more php files  
               - images  
                   - buttons  
                       - button_add_profile.gif  
                       - more gif files  
               - modules  
                   - newsletters  
                       - newsletter.php   
                       - more php files  
- includes  
    - languages  
        - cymraeg.php  
        - cymraeg  
           - account.php  
           - more php files  
           - classic  
               - header.php  
           - extra_definitions  
               - cardinal3dsecure.php  
               - more php files  
               - classic  
                   - empty.txt  
               - responsive_classic  
                   - product_free_shipping.php  
           - html_incldues  
               - define_ask_a_question.php  
               - more php files  
               - classic  
                   - define_checkout_success.php  
                   - more php files  
               - responsive_classic  
                   - define_checkout_success.php  
                   - more php files  
           - images  
               - en_CA.gif  
               - more gif files  
           - modules  
               - order_total  
                   - ot_cod_fee.php  
                   - more php files  
                   - classic  
                       - empty.txt  
               - payment  
                   - authorizenet.php  
                   - more php files  
                   - classic  
                       - empty.txt  
               - shipping  
                   - flat.php  
                   - more php files  
                   - classic  
                       - empty.txt  
           - responsive_classic  
               - icon_names.php  
    - templates  
        - responsive_classic
            - buttons
                - cymraeg
                    - button_update_cart.png
        - template_default  
            - buttons  
                - cymraeg  
                    - button_add_address.gif
                    - more gif files




''Note to translators:'' If you haven't translated the ''Admin'' area, please include the english language files for the ''Admin'' in your language pack so users don't have to experience this.

Additionally but not required, there's the SQL file
:''install/mysql_zencart.sql''
which contains text that will appear on certain ''Admin'' pages. This means that the ''Admin'' area isn't 100% multi-lingual, but this will most likely be dealt with in a future version of Zen Cart&trade;.


You should also include a file named ''README.txt'' where you say something about what has been translated and what has not, along with any other information you feel is appropriate.


{{infoBox|setlocale()|You can specify multiple locales for setlocale():<code><pre><nowiki>setlocale(LC_TIME,
	'english',
	'en_US',
	'en_US.iso_8859-1',
	'en_US.ISO_8859-1',
	'en_US.utf-8',
	'en_US.UTF-8'
);
</nowiki></pre></code>
It makes it easier for users if they don't have to know the correct locale themselves, and we can guess it for them by editing the call to setlocale() in the following files to use the above code:
* ''includes/languages/<your language>.php''
* ''admin/includes/languages/<your language>.php''


== Updating an older translation ==
If a language pack is out of date, you can easily make it up to date by comparing the English language files from the Zen Cart&trade; version that the language pack you wish to update was made for against the English language files of the new Zen Cart&trade; version you wish to update to.


Here's how to do that:
# [http://sourceforge.net/project/showfiles.php?group_id=83781 Download] the Zen Cart&trade; version that matches the original language pack and the Zen Cart&trade; version you wish to update the language pack for.
# Unpack the two packages into two separate directories.
# Open a comparison program like [http://www.scootersoftware.com/download.php Beyond Compare] or [http://winmerge.sourceforge.net/ WinMerge] (for Windows&trade; only)
# Compare the two versions of the directories ''includes/languages and admin/includes/languages'', and be sure to include subfolders.
#* If a file exists only in the older release, delete it from your language pack.
#* If a file exists only in the newer release, copy that English language file into your language pack and translate it.
#* If a file has changed between the two versions, compare those English files to see what exact changes has been made, and update your language pack accordingly.
# Compare the two versions of the directory ''includes/templates/template_default/buttons/english/'' and see if there are any new files. You may also consider updating the images if anyone have changed, but that's probably not strictly necessary.


'''Please share your updated translation with the community. Thank you!'''

== List of known language packs ==
* [http://www.zen-cart.com/downloads.php?do=file&id=855 Arabic v1.3.8]
* [http://www.zen-cart.com/downloads.php?do=file&id=251 Chinese v1.5.1]
* Chinese Traditional [http://www.zen-cart.com/downloads.php?do=file&id=951 Admin v1.3.8] [http://www.zen-cart.com/downloads.php?do=file&id=481 Catalog v1.3.8]
* [http://www.zen-cart.com/downloads.php?do=file&id=146 Czech v1.5.0]
* [http://www.zen-cart.com/downloads.php?do=file&id=891 Danish v1.3.8]
* [http://www.zen-cart.com/downloads.php?do=file&id=1156 Dutch v1.5.0]
* [http://www.zen-cart.com/downloads.php?do=file&id=242 Finnish v1.5.0]
* [http://www.zen-cart.com/downloads.php?do=file&id=62 French v1.3.9]
* [http://www.zen-cart.com/downloads.php?do=file&id=205 German v1.5.1]
* [http://www.zen-cart.com/downloads.php?do=file&id=917 Greek v1.3.8]
* [http://www.zen-cart.com/downloads.php?do=file&id=1657 Hebrew v1.5.1]
* [http://www.zen-cart.com/downloads.php?do=file&id=204 Hungarian v1.3.8]
* [http://www.zen-cart.com/downloads.php?do=file&id=719 Indonesian v1.3.8]
* [http://www.zen-cart.com/downloads.php?do=file&id=161 Italian v1.5.0]
* [http://www.zen-cart.com/downloads.php?do=file&id=284 Japanese v1.3.0]
* [http://www.zen-cart.com/downloads.php?do=file&id=429 Lithuanian v1.3.8]
* [http://www.zen-cart.com/downloads.php?do=file&id=113 Norwegian v1.5.0]
* [http://www.zen-cart.com/downloads.php?do=file&id=1050 Polish v1.5.0]
* [http://www.zen-cart.com/downloads.php?do=file&id=945 Portuguese v1.3.8]
* [http://www.zen-cart.com/downloads.php?do=file&id=194 Romanian v1.5.0]
* [http://www.zen-cart.com/downloads.php?do=file&id=1244 Russian v1.3.9]
* [http://www.zen-cart.com/downloads.php?do=file&id=935 Serbian v1.3.8]
* [http://www.zen-cart.com/downloads.php?do=file&id=432 Slovak v1.3.8]
* [http://www.zen-cart.com/downloads.php?do=file&id=1110 Spanish v1.5.1]
* [http://www.zen-cart.com/downloads.php?do=file&id=1284 Swedish v1.5.1]
* [http://www.zen-cart.com/downloads.php?do=file&id=504 Turkish v1.3.7]
* [http://www.zen-cart.com/downloads.php?do=file&id=857 Vietnamese v1.3.8]

== Language packs ==
The [http://www.zen-cart.com/index.php?main_page=index&cPath=40 download area] is working now, so there shouldn't be any further need of this list.
* [http://www.zen-cart.com/index.php?main_page=index&cPath=40_46 Download language packs]


If you're looking for older versions of Zen Cart&trade; or the default English language files, they can be found at [http://sourceforge.net/project/showfiles.php?group_id=83781 the project's section at sourceforge.net].


'''If you have access to a language pack not listed in [http://www.zen-cart.com/index.php?main_page=index&cPath=40_46 the download area], please [http://www.zen-cart.com/index.php?main_page=add_contrib upload it].'''


=== Wanted translations ===
Feel free to add any languages you would like to see for Zen Cart&trade; here. This could be used to connect people who wants to translate into a certain language, so you might want to leave a way of contacting you if you're willing to participate in translating.


*Arabic
*British-English/Hiberno-English
*Korean
*Vietnamese

== International support sites ==
* [http://www.zen-cart.cn/ Chinese support site]
* [http://www.zen-cart.nl/ Dutch support site]
* [http://www.zen-cart.fr/ French support site]
* [http://www.zen-cart.it/ Italian support site]
* [http://www.zen-cart.jp/ Japanese support site]
* [http://br.groups.yahoo.com/group/zen-cart-pt/ Portuguese support site]
