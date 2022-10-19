---
title: Implementation Guide 
weight: 200
layout: docs
category: release_process
---

The source for the Implementation Guide is in the [private-docs](https://github.com/zencart/private-docs) repo.  The documentation prime should create a PDF version of this file with a name containing the release number, and put it into the /docs folder.

PCI-DSS requires that this guide be: 

- specific for each release
- distributed with the release.

For this reason, the guide is in the /docs folder of the build.  
<!-- and the [Release](/release) folder for the online docs.  --> 

Things to tweak at release time: 

- front page.  When updating the version number, be sure to do it in the footer as well (but not in the Changelog). 

- version number (search and replace).  For example: 
v1.5.7 -> v1.5.8

(In the Changelog at the end, be sure to leave off the "v" so the history won't get accidentally updated.)

- Section 2.4 Server Software Requirements - update versions

- Any other relevant places.

