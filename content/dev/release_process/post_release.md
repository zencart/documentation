---
title: Post-Release tasks 
weight: 90
layout: docs
category: release_process
---

## Post-Release Tasks for the Zen Cart Forum 
- Add the new version to the Zen Cart Version dropdown on the forum for new thread creation. (Note that this is not required for patch releases.)

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

- Add the new version as a checkbox to the plugin version list. (Note that this is not required for patch releases.)

<img src="/images/plugin_version_selection.png"> 
<br><br>

Instructions: 
```
- Login to the admin panel for zen-cart.com

- Maintenance -> Execute SQL Query 

insert into vb_dl2_zcversions (versiontext) values ('v1.5.8')
```

## Other Post-Release Tasks 

- Update the [Release History](/user/about_us/release_history/) page with the new version and date.

- Create a "Known Bugs in <release>" thread on the [Upgrading to 1.5.x subforum](https://www.zen-cart.com/forumdisplay.php?156-Upgrading-to-1-5-x).   Update the release announcement and the [known bugs](/user/about_us/known_bugs/) page with this link.

- Search the documentation in https://github.com/zencart/documentation for the string RELEASETIME and update those files.

- Run the `build_doc` and `view schema` tools as noted in the [Release Time](https://github.com/scottcwilson/zencart_tools). 

- **Emergency Re-release:** If something was missed and you have to do a re-release, go back to [Remedial Commits](/dev/release_process/release_tagging/#possible-remedial-commits). 

A day or two after the build has been released when you're confident that all is well: 

- Message all developers who have merge privileges using the Skype Dev Chat channel, and then unlock the branch you are building.  Go to [the branches page](https://github.com/zencart/zencart/settings/branches) and de-activate the branch protection rule you created earlier (uncheck the "PR required" checkbox for the rule).

- Begin process of formally merging release to Master/Main **FIXME - unsure**

- Take some time to review the What's New document in the [release folder](/release) to be sure it's complete. 

