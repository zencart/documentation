---
title: How do I set up and report on banner ads? 
description: Banner management in admin 
category: admin
weight: 10
---

You can control your banners in [Admin > Tools > Banner Manager](/user/admin_pages/tools/banner_manager/). 
You will see that you can add delete and edit the banners at will.

To add a new banner, click the `New Banner` button.
To edit an existing one and change its link, its picture, etc, click on the banner you want to change, and click the `Edit` button.

You can enable and disable any particular banner by clicking on the red/green status button.
You might want to set the banner status to off for banners you don't want to show until you are more familiar with them so you can use them as examples. You are not obligated to show any of the banners distributed with Zen Cart.

### BANNER STYLES
There are 2 styles of banners: sidebox and wide banners

Sidebox banners are narrower and designed to fit in a sidebox.
Wide Banners are designed to span the width of your page.  The images should be wide, but not too tall.

You can give almost whatever group name you want to a banner. Banners in the same group will be randomly displayed one at a time in the position indicated in `Layout Settings` (see below).


#### POSITIONING BANNER GROUPS
You control which group of banners is "displayed where" by editing the "Banner Display Groups" position group names under [Admin > Configuration > Layout Settings](/user/admin_pages/configuration/configuration_layoutsettings/).

Displaying MORE THAN ONE Banner within a group at a time. The BannersAll group is designed for "1-to-many" static banners.
You can only use 1 Banner Group on this particular sidebox, unlike the other banners where you can have multiple Banner Groups.
I called it BannersAll so it would be easy to remember.
Add your banner(s) just like you normally would and add to the BannersAll Group
If BannersAll is not in your list in the dropdown type it in so it will be for now on.
If you do not have the BannersAll defined for the Layout Settings for the following, do so now:
`Banner Display Group - Side Box banner_box_all`

If using multiple banners and you would like them to appear in a particular order add the sort order to them.
I number these 10, 20, 30 etc. so that I can easily insert new ones in between without having to renumber them all in the future.

Note: you can have a bazillion Banner Groups defined and put them together in the 8 various banner positions.

It is the BannersAll that is the only exception to this rule.

Banner sizes are your choice as well. There are Internet standard sizes for consistency, but you can make them any size that you want and mix and match the sizes depending on your layout.


#### DISPLAYING BANNER GROUPS IN YOUR TEMPLATE

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

For more information, under the "Action" column, you see a small white graph symbol. Click on that to view stats for day/month/year.

