---
title: Release tagging
weight: 50
layout: docs
category: release_process
---
We are now ready to tag the release.

Ensure your Zen Cart folder is up to date, especailly
as you will have merged the version stamping changes.

Now we tag the release 

`git tag v1.5.8-alpha` obviously replacing the release name as appropriate

`git push upstream --tags`

It may be that you may need to do some remedial commits at this point.

**For any new commits at this point, we should manually update headers as 
it is difficult to re-run the version stamper. You may also need to update `docs`
and your [Release Notes]({{< ref "release_notes" >}} "release notes") as well.**

If you have added extra commits you will need to update the release tag.

```
git tag -d v1.5.8-alpha
git push --delete upstream v1.5.8-alpha
git tag v1.5.8-alpha
git push upstream --tags
```

After this we then need to create the release on github.

https://github.com/zencart/zencart/tags

![ Github Tags](/images/github-tags_page_zencart.png)

By clicking on the ... on the far right hand side we can create a release.

![Github Create Release](/images/github_create_release_zencart.png)


The title is usually the same name as the tag name.

For Pre-Releases: 
- Don't forget to check the pre-release box 

For Official Releases: 
- The textarea below the Release title should reference the the https://docs.zen-cart.com release documentation.


