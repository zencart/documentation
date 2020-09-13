---
title: How do I validate the integrity of a downloaded file? 
description: Checking SHA1 or MD5 checksums 
category: installing 
weight: 10
---

When downloading files from the internet, it's very important to verify that the file you downloaded IS in fact the file you EXPECTED to download. Authors of software typically zip up their software and then calculate a "checksum" based on the contents, and post that checksum next to the link to download the file. YOU should then re-calculate the checksum on the file AFTER downloading, and compare to be sure that the checksum YOU calculated matches the one posted by the author. If they don't match, then you should NOT use the downloaded file, because it may have been tampered with. In such cases you should also report the discrepancy to the author so they can investigate the tampering or fix a mistake.

See [the useful tools page](/user/first_steps/useful_tools/#hash-validation-tools) for a list of checksum validation tools. 

