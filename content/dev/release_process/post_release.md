---
title: Post-Release tasks 
weight: 90
layout: docs
category: release_process
---

## Post-Release Tasks for the Zen Cart Forum 

### Add the new version to the Zen Cart Version dropdown on the forum

(Note that some steps will not be required for patch releases or pre-releases.)

<img src="/images/forum_version_selection.png"> 
<br><br>

Instructions: 
```
- Login to the admin panel for zen-cart.com
- Thread Prefixes -> Thread prefix manager 
- Where it says "Zen Cart version", click on Add Prefix 
```

<img src="/images/thread_prefix_manager.png"> 
<br><br>

```
then set prefix id, title (both) to the version 
e.g. v158
leave display order as 10 
click Save
```

### Add the new version as a checkbox to the plugin version list. 

(Note that this is not required for patch releases.)

<img src="/images/plugin_version_selection.png"> 
<br><br>

Instructions: see the 
[infrastructure repo](https://github.com/zencart/infrastructure).  (Team members only.)

## Other Post-Release Tasks 

### All Releases 

- Update the [Release History](/user/about_us/release_history/) page with the new version and date.  (Skip this step for pre-releases.)

- Update the [What's New with Zen Cart](/user/about_us/whats_new/) page.

### Major and Minor Releases Only

- Create a "Known Bugs in <release>" thread in the appropriate subforum under [Upgrading Your Zen Cart](https://www.zen-cart.com/forumdisplay.php?10-Upgrading-Your-Zen-Cart).   Update the release announcement and the [known bugs](/user/about_us/known_bugs/) page with this link.

If you need to create a new subforum ("Updating to Y.x.x"), follow the guidance on the [infrastructure repo](https://github.com/zencart/infrastructure).  (Team members only.)

- Update the file `.github/security.md` in the main Zen Cart repo if needed.

- Ensure the [Release Specific Upgrade Considerations](/user/upgrading/release_specific_upgrade_considerations/) doc has a statement about this release.

- Update the pages in [Third Party Libraries](/dev/libraries/) if any major library version changes have been made.

- Search the documentation in https://github.com/zencart/documentation for the string RELEASETIME and update those files.

- Search the documentation for "NOT RELEASED YET" - if this is for the release you just built, remove it.

- Run the `build_doc` and `view schema` tools.
   - `build_doc` is in the [Zen Cart Tools](https://github.com/scottcwilson/zencart_tools) repo.  It creates the [configuration documentation](https://docs.zen-cart.com/user/admin_pages/configuration/).  Install it in the `admin` folder for the new release, edit the file and set `TARGET_FOLDER`, then run it; it will update the Zen Cart documentation folder. 
   - `view_schema` is a plugin located [here](https://www.zen-cart.com/downloads.php?do=file&id=2270). It creates the [schema documentation](https://docs.zen-cart.com/dev/schema/).  Install the plugin, then do an Inspect in Google Chrome on the output and copy the element with id="pageWrapper" into a new file in `zencart_documentation/content/dev/schema`.  Remove the opening and closing div tags, and copy in the Hugo frontmatter and styling from the prior schema file.

- **Emergency Re-release:** If something was missed and you have to do a re-release, go back to [Remedial Commits](/dev/release_process/release_tagging/#possible-remedial-commits). 

A day or two after the build has been released when you're confident that all is well: 

- Message all developers who have merge privileges using the Skype Dev Chat channel, and then unlock the branch you are building.  Go to [the branches page](https://github.com/zencart/zencart/settings/branches) and de-activate the branch protection rule you created earlier (uncheck the "PR required" checkbox for the rule).  Note that this can be done much sooner for a pre-release. 

- Take some time to review the What's New and Changed Files documents in the [release folder](/release) to be sure they are complete. 

## One more documentation check:
- Review the What’s New file for this release (Documentation repo in the `/release/` folder.)  Be sure it doesn't have any more statements like "*New Version* has not yet been released".
- Review the Changed Files list for this release (Documentation repo in the `/release/` folder.)  Same checks.


## Post-Release Things to Consider 

- Is it time to remove old versions from the plugin version list?

- Is it time to hide older what's new / changed files documents in the [release](/release) folder? 

- Are there old stuck posts on the forum that should be unstuck? 

- Check the Zen Cart and Zen Cart Documentation projects for tags that mark things that need to be taken care of - there might be a 'Post Release X.y.z' tag or something like that, for example. 

