---
title: Ping Server
weight: 60
layout: docs
category: release_process
---

Note: if you are doing a pre-release rather than an official release, please skip this step and go to the [next step](#next). 

The ping server([ping.zen-cart.com](https://ping.zen-cart.com)) is an endpoint that allows for a call home from within Zen Cart admin.

It will notify a shop owner if a new release is available.

You need to have login access to https://ping.zen-cart.com/dashboard

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


<div style="text-align:right;" id="next">
   <a class="btn btn-lg btn-primary mr-3 mb-4" href="/dev/release_process/release_links/">
        Next - Release Links<i class="fas fa-arrow-alt-circle-right ml-2"></i>
   </a>
</div>
