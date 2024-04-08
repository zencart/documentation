---
title: Server Manager
weight: 60
layout: docs
category: release_process
---

Note: if you are doing a pre-release rather than an official release, please skip this step and go to the [next step](/dev/release_process/release_links/). 

The Server Manager controlls the endpoint that allows for a call home from within Zen Cart admin.  (It was formerly called the Ping Server, or `ping.zen-cart.com`.) 

It will notify a shop owner if a new release is available.

You need to have login access to https://servermanager.zen-cart.com/

![Server Manager](/images/sm_dashboard.png)

and then access the `Version Manager > Versions` menu.

We can then create a new release by clicking the "New Version" button.

![ Ping Version Edit](/images/sm-version-edit.png)

For a full release we need to edit 

+ Version major
+ Version minor
+ Version detail
+ Version download url

## Version major

Currently this will be 2.

## Version minor

e.g. 0.0

## Version detail

Link to release announcement (e.g. https://www.zen-cart.com/showthread.php?230040-Zen-Cart-2-0-0-Released)

## Version download url

Link to download (e.g. https://github.com/zencart/zencart/archive/refs/tags/v2.0.0.zip)

## is_current
Turn slider on

<div style="text-align:right;" id="next">
   <a class="btn btn-lg btn-primary mr-3 mb-4" href="/dev/release_process/release_links/">
        Next - Release Links<i class="fas fa-arrow-alt-circle-right ml-2"></i>
   </a>
</div>
