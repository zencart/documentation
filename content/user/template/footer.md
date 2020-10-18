---
title: Site Footer 
description: How can I change my storefront footer layout? 
category: template
weight: 10
---

The storefront footer is content that will appear at bottom top of every page. 

![Footer](/images/footer.png) 

<br>

The links in the black background are created by `includes/templates/YOURTEMPLATE/templates/ezpages_bar_footer.php`. 

The display of IP Address information is controlled by *Footer - Show IP Address status* in [Admin > Configuration > Layout Settings](/user/admin_pages/configuration/configuration_layoutsettings/). 

The Copyright string is uses the defined constant `FOOTER_TEXT_BODY` from `includes/languages/YOURTEMPLATE/english.php`. 

On a mobile device, the layout is much simpler; just the IP Address and copyright string, as well as a banner if [footer banners](/user/admin_pages/tools/banner_manager/) are used. 

![Mobile Footer](/images/mobile_footer.png)

