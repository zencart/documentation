---
title: Banner Manager
category: admin_pages
weight: 10 
---

This page manages your cart's [banners](/user/admin/banner_ads/) - individual text and image banners and their groups.  When the screen is opened, a list of existing banners is displayed. 

![Banner Manager](/images/banner_manager.png)

Each banner (text or image) belongs to a banner group.  Having multiple banners in a banner group allows different banners to be displayed in rotation at the same position.

The position of a Banner Group on the shopfront page is defined in the [Layout Settings](/user/admin_pages/configuration/configuration_layoutsettings/) page. 

Three banner groups come with Zen Cart: 
- Wide-Banners
- Sidebox-Banners
- BannersAll 

Banner Positions are provided by your template.  There are:

- three positions in the header (positions 1, 2 and 3), 
- three positions in the footer (positions 1, 2 and 3), 
- three sidebox positions (banner_box, banner_box2 and banner_box_all). 

Generally you would choose at most one of these positions in each area. 

These positions can be seen in this diagram from @lat9: 

![Banner Positions](/images/banner_positions.jpg)

Groups are then specified in the *Banner Display Groups* settings in [Admin > Configuration > Layout Settings](/user/admin_pages/configuration/configuration_layoutsettings/).  For example, setting *Banner Display Groups - Footer Position 3* to *Wide-Banners* means that a banner in the Wide-Banners group will be shown in Footer Position three. Here's what that looks like: 

![Wide Banner Footer Position 3](/images/banner_footer_position_3.png)

Similarly, turning on the [banner_box sidebox](/user/sideboxes/sidebox_list/) and setting *Banner Display Groups - Side Box banner_box* to *Sidebox-Banners* means that a banner will be selected from the Sidebox-Banners group and shown in the banner_box sidebox. 

To add a new banner, press the *New Banner* button at the bottom of the Banner Manager screen. 

![New Banner](/images/new_banner.png)

Tips: 

- Some users like to name banner groups by size, using group names like HalfWidth, FullWidth, and so forth.  Others like to name banner groups by placement, using group names like BanHeadPos1, BanHeadPos2, BanHeadPos3, BanFootPos1, BanFootPos3, BanFootPos3.

- Empty banner groups are deleted. Adding a banner group is done by specifying the group name in the text field below the Banner Group dropdown on the New Banner screen. Once a Banner Group is added, the new name will appear in the dropdown.

