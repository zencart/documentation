---
title: Ping Server
weight: 60
layout: docs
category: release_process
---

The ping server([ping.zen-cart.com](https://ping.zen-cart.com)) is an endpoint that allows for a call home from within Zen Cart admin.

It will notify a shop owner if a new release is available.

Currently you need SSH access to the Ping Server to update these details.

Details are in /var/www/html/versionServer/config/zcversion.php

```return [
    'versionMajor' => '1',
    'versionMinor' => '5.7d',
    'versionDetail' => 'Security + PHP8 fixes',
    'versionPatch1' => '0',
    'versionPatch2' => '0',
    'versionPatchDetail' => 'Recommended Upgrade',
    'versionDownloadURI' => 'https://www.zen-cart.com/showthread.php?228675-Zen-Cart-v1-5-7d-released!!',
];
```

For a full release we only need to edit 

+ versionMajor
+ versionMajor
+ versionDetail
+ versionDownloadURI

## versionMajor

Currently this will always be 1.

## versionMinor

e.g. 5.7.d

## versionDetail

A brief description of the new release.

## versionDownloadURI

Generally a link to the release announcement.
e.g. https://www.zen-cart.com/showthread.php?228675-Zen-Cart-v1-5-7d-released!!
