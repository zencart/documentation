---
title: Release Links
weight: 70
layout: docs
category: release_process
---

Note: if you are doing a pre-release rather than an official release, please skip this step and go to the [next step](/dev/release_process/manifest/). 

Release links are placed on the [Home page](https://www.zen-cart.com) of the Zen Cart Web Site.

![ Download Links](/images/download_links.png)

To change the links etc, you will need `admin` permissions for the Zen Cart forum.

![ Frontpage edit](/images/frontpage_edit.png)

Clicking on the edit icon in the top right will allow you to change the front page details.

The actual content that manages the release information looks like 

```html

<div class="vbcms_content" style="width:100%;">
    <div class="my_right_box"  style="width:33%;text-align:center;float:right;">
      <img src="/images/styles/zencart/style/ZC-in-the-box.jpg">
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

The areas that need changing are: 

- release announcement
- download link 
- SHA

To determine the SHA value, download the release zip from Github, and compute the SHA with the appropriate method for your platform. 

- MacOS: `shasum -a 256  ./zencart-1.5.8.zip`
- Linux: ` sha256sum zencart-1.5.8.zip`

<div style="text-align:right;" id="next">
   <a class="btn btn-lg btn-primary mr-3 mb-4" href="/dev/release_process/manifest/">
        Next - Release Manifests<i class="fas fa-arrow-alt-circle-right ml-2"></i>
   </a>
</div>
