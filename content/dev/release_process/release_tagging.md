---
title: Release tagging
weight: 50
layout: docs
category: release_process
---
We are now ready to tag the release.

You should already have a checkout of the release branch. Ensure this is up to date, especailly
as you will have merged the version stamping changes.

Now we tag the release 

`git tag v1.5.8-alpha` obviously replacing the release name as appropriate

`git push upstream --tags`

It may be that you may need to do some remedial commits at this point.

**Note for any new commits at this point we should manually update headers as 
it is difficult to re-run the version stamper. You may also need to update `docs`as well.
**

Remember to update your [Release Notes]({{< ref "release_notes" >}} "release notes") as well.

If you have added extra commits you will need to update the release tag.

`git tag -d v1.5.8-alpha`
`git push --delete upstream v1.5.8-alpha`
`git tag v1.5.8-alpha`
`git push upstream --tags`


After this we then need to create the release on github.

https://github.com/zencart/zencart/tags

![ Github Tags](../../static/images/github-tags_page_zencart.png)

By clicking on the ... on the right hand side we can create a release.

![Github Create Release](../../static/images/github_create_release_zencart.png)


The title is usually the same name as the tag name.

The description should point the the https://docs.zen-cart.com release documentation

Don't for get to mark it as a pre-release if necessary.
