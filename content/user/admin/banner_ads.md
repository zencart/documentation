---
title: How do I set up banners? and report on banner ads? 
description: Banner management in admin 
category: admin
weight: 10
---

## Banner Manager - Quick Summary
You can control/add/edit/delete your banners in [Admin > Tools > Banner Manager](/user/admin_pages/tools/banner_manager/). (click this link for more details)

To add a new banner, click the `New Banner` button.
To edit an existing one and change its link, picture, etc, click on the banner you want to change, and click the `Edit` button.

You can enable and disable any particular banner by clicking on the red/green status button.

You might want to set the banner status to off for banners you don't want to show until you are more familiar with them so you can use them as examples. 

You are not obligated to show any of the banners distributed with Zen Cart.

Images used in banners are typically uploaded to your server's `/images/banners` directory.


## Banner Styles
There are 2 styles of banners: **sidebox** banners and **wide** banners

[Sidebox Banners](/user/sideboxes/sidebox_list/#banners) are narrower and designed to **fit in a sidebox**.

Wide Banners are designed to **span the width of your page**.  The images should be wide, but not too tall.

You can give almost whatever group name you want to a banner. Banners in the same group will be randomly displayed one at a time in the position indicated in `Layout Settings` (see below).

### Banner Sizes

Banner sizes are your choice. There are industry standard "ad" sizes you could consider for the sake of consistency, but you can make them any size that you want and mix and match the sizes depending on your layout.

Keep in mind that using industry-standard sizes might get your banners treated as "ads" and therefore ad-blocking browser plugins might hide them.


### Positioning Banner Groups
You control which group of banners is "displayed where" by editing the "Banner Display Groups" position group names under [Admin > Configuration > Layout Settings](/user/admin_pages/configuration/configuration_layoutsettings/).

If you assign more than one banner to a certain group, it will randomly pick one from that group whenever that group is asked to be displayed.

Only one banner is displayed at a time in any banner position. (There is an exception to this: the BannersAll sidebox, which displays all banners assigned to its group, in the sort order you specify.)


#### Banner Locations in Templates

In the default template the following are where these banners will be displayed:

<img src="/images/banners_header.png" alt="Header Positions for Banner Groups">

<img src="/images/banners_footer.png" alt="Footer Positions for Banner Groups">


#### Technical note for coders:

By default the banner groups are internally numbered and displayed using template parameters as follows:

```
Banner Display Groups - Header Position 1 = SHOW_BANNERS_GROUP_SET1
Banner Display Groups - Header Position 2 = SHOW_BANNERS_GROUP_SET2
Banner Display Groups - Header Position 3 = SHOW_BANNERS_GROUP_SET3
Banner Display Groups - Footer Position 1 = SHOW_BANNERS_GROUP_SET4
Banner Display Groups - Footer Position 2 = SHOW_BANNERS_GROUP_SET5
Banner Display Groups - Footer Position 3 = SHOW_BANNERS_GROUP_SET6
Banner Display Groups - Side Box banner_box = SHOW_BANNERS_GROUP_SET7
Banner Display Groups - Side Box banner_box2 = SHOW_BANNERS_GROUP_SET8
Banner Display Groups - Side Box banner_box_all = SHOW_BANNERS_GROUP_SET_ALL
```


### How do I generate a report on banner advertising? 

Banner statistics are tracked on an ongoing basis. When you open [Admin > Tools > Banner Manager](/user/admin_pages/tools/banner_manager/), you can see the last 3 days' details on-screen.  

For more information, under the "Action" column, you see a small icon of a chart. 

![Chart icon](/images/chart_icon.png)

Click on that icon to view [Banner Statistics](/user/admin_pages/tools/banner_statistics/) for day/month/year.

