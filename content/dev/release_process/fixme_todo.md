---
title: Still to Document
weight: 90
layout: docs
category: release_process
---
# Still to doc

 + Updating ping server details 
 + Updating release links on https://www.zen-cart.com with SHA hashes and links to forum post
 + updating manifest files on version server

 + update AWS version-server files, and invalidate them on Cloudfront
 + upload zip to AWS zencart-download dir, and make public
 + update forum .htaccess to point to new latest_https on AWS, including version/date hash/suffix

For non-lettered-releases:
 + update forum Plugins area to accept this new version (update zcversions db table)
 + update forum "Prefixes" to add new release, in next-lowest sort order.

 + update any Notifications Banners in the VersionServer database and PAN server database
