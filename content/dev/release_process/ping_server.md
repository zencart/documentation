---
title: Ping Server
weight: 60
layout: docs
category: release_process
---

The ping server([ping.zen-cart.com](https://ping.zen-cart.com)) is an endpoint that allows for a call home from within Zen Cart admin.

It will notify a shop owner if a new release is available.

You need to gave been given login access to https://ping.zen-cart.com/dashboard

and then access the `versions` menu.

![ Ping Server Dashboard](/images/ping-version-menu.png)

We can then create a new release.

![ Ping Version Edit](/images/ping-version-edit.png)

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

## is_current

