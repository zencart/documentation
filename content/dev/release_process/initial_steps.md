---
title: Initial Steps
weight: 30
layout: docs
category: release_process
---
The initial phase of the release process consists of

 + Locking the repository for merges
 + Ensuring all code is up to date
 + tagging the release


# Locking Repository

While doing the initial steps of process release, at least up to the tagging release stage,
we need to ensure that no commits/merges are created against the release branch and the main branch,
except where necessary for the release.

Message all developers who have merge privileges using the Skype Dev Chat channel, and then lock the branch you are building.  Go to [the branches page](https://github.com/zencart/zencart/settings/branches) and set a branch protection rule.  Here is a list of [branch protection rules for 158](https://github.com/zencart/zencart/settings/branch_protection_rules/26951040) for example.  Click on the checkbox for *Require a pull request before merging*
then set the required approvals to 6, and the branch will be effectively locked.  


# Updating Code

Before tagging a release we need to ensure code is up to date.

We need to update the [Documentation Website](https:docs.zen-cart.com/release) to ensure that it reflects changes that have happened within
the release and stamp files that have been changed/added with correct copyright and other headers.

# Release Documentation

The [Documenation Website](https:docs.zen-cart.com/release)  contains details of changes between versions and general installation instructions.

The 2 main pages that need adding/updating are the [Whats New](https://docs.zen-cart.com/release/whatsnew_1.5.7.html)
and [Changed Files](https://docs.zen-cart.com/release/changed_files-v1-5-7.html) pages.
Note: The above links give examples of previous releases.

You will need to have checkout of the Zen Cart documentation website and be able to use the Hugo system to
edit and test the pages locally before pushing changes,

While previously we would duplicate content in the `/docs` folder of the release and on the
https://zen-cart.com/docs folder, these now redirect to the documentation website.
