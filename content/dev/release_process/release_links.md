---
title: Release Links
weight: 70
layout: docs
category: release_process
---

Note: if you are doing a pre-release rather than an official release, please skip this step. 

Before updating release links, you should create a release announcement thread on the forum.

https://www.zen-cart.com/newthread.php?do=newthread&f=2

[An example release announcement](https://www.zen-cart.com/showthread.php?228675-Zen-Cart-v1-5-7d-released!)

**When creating the release announcement, you should create it as a sticky announcement**

Release links are placed on the [home page](https://www.zen-cart.com) of the Zen Cart Web Site.

![ Download Links](/images/download_links.png)

To change the links etc, you will need `admin` permissions for the Zen Cart forum.

![ Frontpage edit](/images/frontpage_edit.png)

Clicking on the edit icon in the top right will allow you to change the front page details.

The actual content that manages the release information looks like 

```html

<div class="vbcms_content" style="width:100%;">
    <div class="my_right_box"  style="width:33%;text-align:center;float:right;">
        <a href="https://github.com/zencart/zencart/archive/refs/tags/v1.5.7d.zip" target="_blank"><img src="/images/styles/zencart/style/ZC-in-the-box.jpg"></a>
<div style="font-size:14px;margin-bottom:20px"><a href="https://www.zen-cart.com/showthread.php?228675-Zen-Cart-v1-5-7d-released!!">v1.5.7d Release Announcement</a></div>
<a target="_blank" href="https://github.com/zencart/zencart/archive/refs/tags/v1.5.7d.zip" style="display:block">
<div class="dlButton"><p class="verBubble"><span class="verNum">v1.5.7d</span></p> Download Zip File</div>
</a>

<br />

<div style="font-size:10px;margin-bottom:20px">SHA256: 0b115b58745cd09a0e4ae2795df437f051552d453ff9d0d9f333d96685836294</div>

<div style="font-size:10px;margin-bottom:20px">Tip: Use the SHA checksum shown to <a href="https://docs.zen-cart.com/user/installing/validate_sha/" target="_blank">verify file integrity</a></div>

<p style="font-size:14px;"><a href="https://docs.zen-cart.com/history/v15x/" target="_blank">Click here to download older versions</a></p>
<p style="font-size: 14px;"><a href="https://www.zen-cart.com/docs/" target="_blank">Implementation Guide</a></p>

    </div>
```

The areas that need changing are ...

```html
<a href="https://github.com/zencart/zencart/archive/refs/tags/v1.5.7d.zip" target="_blank"><img src="/images/styles/zencart/style/ZC-in-the-box.jpg"></a>
<div style="font-size:14px;margin-bottom:20px"><a href="https://www.zen-cart.com/showthread.php?228675-Zen-Cart-v1-5-7d-released!!">v1.5.7d Release Announcement</a></div>
<a target="_blank" href="https://github.com/zencart/zencart/archive/refs/tags/v1.5.7d.zip" style="display:block">
```

where the hrefs need updating to point to the release zips on gitub and the forum relese announcement thread.

and 

```html
<div style="font-size:10px;margin-bottom:20px">SHA256: 0b115b58745cd09a0e4ae2795df437f051552d453ff9d0d9f333d96685836294</div>
```

where the SHA needs to be updated.

