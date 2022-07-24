---
title: Initial Steps
weight: 30
layout: docs
category: release_process
---
# Initial Steps

The initial phase of the release process consists of

 + Locking the repository for merges
 + Ensuring all code is up to date
 + tagging the release


# Locking Repository

While doing the initial steps of process release, at least up to the tagging release stage,
we need to ensure that np commits/merges are created against the release branch and the main branch,
except where necessary for the release.

The simplest way of doing this is to communicate with all developers who have merge priveleges.

Would suggest using the Skype Dev Chat channel for this.

# Updating Code

Before tagging a release we need to ensure code is up to date.

We need to update the [Documenation Website](https:docs.zen-cart.com/release) to ensure that it reflects changes that have happened within
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
