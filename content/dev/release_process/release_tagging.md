---
title: Release tagging
weight: 50
layout: docs
category: release_process
---
We are now ready to tag the release.

Ensure your Zen Cart folder is up to date, especailly
as you will have merged the version stamping changes.

Now we tag the release.

### Prerequisites
If you have not pulled the current list of tags, do so now: 

```
git fetch --tags
```

You can confirm your local copy of tags using 

```
git tag --list
```

### Tagging 

**Note:** The tag *must* be the same as the `newVersion` setting in the versionstamper's `config.php` file. 

`git tag v1.5.8` obviously replacing the release name as appropriate

`git push upstream --tags`

### Possible Remedial Commits 

After creating the release on Github (the next step), you will want to test the build and make sure it works.  
If you test the resultant build, and find a problem, 
it may be that you may need to do some remedial commits at this point.

**For any new commits at this point, you must manually update headers as 
it is difficult to re-run the version stamper.**

- Edit files to update headers - change date and committer name
- Create PR, merge, update your branch

If you have added extra commits you will need to update the release tag.

```
git tag -d v1.5.8
git push --delete upstream v1.5.8
git tag v1.5.8
git push upstream --tags
```

Then re-run these steps of the build: 
- Create the release on Github (as noted below). 
- Note new commit hash and update [Release Log]({{< ref "release_log" >}} "release log") 
- Update the [zip file SHA on the home page](/dev/release_process/release_links/).
- Update the [Release Manifest](/dev/release_process/manifest/)
- Check the [Releases Page](https://github.com/zencart/zencart/releases) and be sure the build you just did is Published and the old one is removed.
- If required, update `docs` (What's New file, Changed Files).

### Create the Release on Github

After this we then need to create the release on github.

https://github.com/zencart/zencart/tags

![ Github Tags](/images/github-tags_page_zencart.png)

By clicking on the ... on the far right hand side we can create a release.

![Github Create Release](/images/github_create_release_zencart.png)


The title should be the same name as the tag name.

For Pre-Releases: 
- Don't forget to check the pre-release box 

For Official Releases: 
- The textarea below the Release title should reference the https://docs.zen-cart.com release documentation.

It's a good idea to also check the "Create a discussion for this release" box. 

When you're ready, press the **Publish Release** button.

### Verification 
Take some time to verify the build you just published.  Since you already did pre-testing before beginning the build process, hopefully there will be no issues, but if there are, return to the [Possible Remedial Commits](/dev/release_process/release_tagging/#possible-remedial-commits) step. 

### Additional Release Tasks: 

- update the What's New and Changed Files documents for the release in [zencart_documentation/content/release](https://docs.zen-cart.com/release/).

- Create a release announcement on the Zen Cart Forum.  Create it as a sticky post.  Here is an [example release announcement](https://www.zen-cart.com/showthread.php?229041-Zen-Cart-1-5-8-Released!).   

<div style="text-align:right;" id="next">
   <a class="btn btn-lg btn-primary mr-3 mb-4" href="/dev/release_process/ping_server/">
        Next - Ping Server<i class="fas fa-arrow-alt-circle-right ml-2"></i>
   </a>
</div>
