---
title: Adding Team Members 
weight: 999
layout: docs
category: release_process
---

Steps for giving out privileges for various capabilities: 
- core committers who can do merges 
- people who can run the build
- moderators and plugin moderators 
- issue assignees 

### Adding someone to zen-cart.com admin 

This is required for the [Post-Release Tasks for the Zen Cart Forum](/dev/release_process/post_release/#post-release-tasks-for-the-zen-cart-forum) step in the release process. 

- Login to the admin panel for zen-cart.com. 
- In Users > Search for Users, find their account.  
- Edit their Usergroup Options to make them an Administrator. 
- Verify that you have the link Usergroups > Administrator Permissions.  If you don't have this link, ssh to Reynolds and edit the `includes/config.php` file.  Add your id (numeric account number, not user name) to the line that begins with `$config['SpecialUsers']['superadministrators']`. 
- In Usergroups > Administrator Permissions, click Edit Permissions for their account.  Click the "All Yes" button on the upper right. 

### Adding somone to the Github core committers list 

This is required for merging PRs and doing the [Release Tagging](/dev/release_process/release_tagging/) step in the release process.  

Login to Github and go to the [Zen Cart committers member list](https://github.com/orgs/zencart/teams/committers/members).  Press the "Add a member" button.

The documentation site has its own core committers list, called [doc-collaborators](https://github.com/orgs/zencart/teams/doc-collaborators/members).  The same process is used to add new members to that list.

### Allowing somone to ssh to Reynolds

This is not required for all members, but may be useful in case vBulletin needs to be modified in some way.  An example is adding a super administrator, as noted above - this cannot be done in the vBulletin UI; it requires a file change.

Give them the server IP, port and passphrase and have them create a key for passwordless ssh. 

### Allowing someone to update the PingServer 

This is required for the [Ping Server ](/dev/release_process/ping_server/) 
and [Release Manifests](/dev/release_process/manifest/) steps in the release process. 

Login to [Ping Server Dashboard](https://ping.zen-cart.com/dashboard) and click the team name on the upper right, then click Team Settings.  Adding a Team Member is the second dialog on the page. 

### Making someone a forum moderator 

- Login to the admin panel for zen-cart.com. 
- In Users > Search for Users, find their account.  
- Edit their Usergroup Options to make them a Moderator.

### Making someone a plugin moderator 

- Login to the admin panel for zen-cart.com. 
- In Users > Search for Users, find their account.  
- Edit their Usergroup Options to make them a Plugins/Addons Moderator.

### Assigning someone an issue in Github 

Github does not permit you to assign an issue to any arbitrary user. 
Issues may only be assigned to 
- the user who opened the issue
- a user who commented on an issue 
- a member of the [Github ZenCart Contributors](https://github.com/orgs/zencart/teams/contributors/members) team.

To add someone to the Github ZenCart Contributors team, invite them using the "Add a member" button on the [Contributors team page](https://github.com/orgs/zencart/teams/contributors/members).  Once they accept, they will appear in the list of members.  You can learn more about how this process works by reading [these instructions from Github](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/managing-teams-and-people-with-access-to-your-repository). 

