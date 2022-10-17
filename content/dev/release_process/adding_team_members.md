---
title: Adding Team Members 
weight: 999
layout: docs
category: release_process
---

Steps for adding new core committers who can do merges and run the build. 

### Adding them to ZenMissionControl

This is required for the [Post-Release Tasks for the Zen Cart Forum](/dev/release_process/post_release/#post-release-tasks-for-the-zen-cart-forum) step in the release process. 

- Login to ZenMissionControl. 
- In Users > Search for Users, find their account.  
- Edit their Usergroup Options to make them an Administrator. 
- Verify that you have the link Usergroups > Administrator Permissions.  If you don't have this link, ssh to Reynolds and edit the `includes/config.php` file.  Add your id (numeric account number, not user name) to the line that begins with `$config['SpecialUsers']['superadministrators']`. 
- In Usergroups > Administrator Permissions, click Edit Permissions for their account.  Click the "All Yes" button on the upper right. 

### Adding them to the Github core committers list 

This is required for  

Login to Github and go to the [Zen Cart committers member list](https://github.com/orgs/zencart/teams/committers/members).  Press the "Add a member" button.


### Allowing them to ssh to Reynolds

This is not required for all members, but may be useful in case vBulletin needs to be modified in some way.  An example is adding a super administrator, as noted above - this cannot be done in the vBulletin UI; it requires a file change.

Give them to OpenSSH passphrase and have them create a key for passwordless ssh. 
### Allowing them to update the PingServer 

This is required for [the Ping Server step](/dev/release_process/ping_server/) in the release process. 

Login to [Ping Server Dashboard](https://ping.zen-cart.com/dashboard) and click the team name on the upper right, then click Team Settings.  Adding a Team Member is the second dialog on the page. 

### Making them a plugin moderator 

- Login to ZenMissionControl. 
- In Users > Search for Users, find their account.  
- Edit their Usergroup Options to make them a Plugins/Addons Moderator.

