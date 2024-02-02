---
title: Github Workflow + Pull Requests
description: Best practices for managing and submitting PRs 
weight: 3
---

This article is intended to help provide a basic understanding of contributing to forked repositories on github, including forking, updating your local copy, and **making Pull Requests**.

## Quick Reference for Newcomers to git or github

For the basics of learning git, see: [https://help.github.com/categories/bootcamp/](https://help.github.com/categories/bootcamp/)

For the basics of learning github, see: [https://help.github.com/articles/good-resources-for-learning-git-and-github/](https://help.github.com/articles/good-resources-for-learning-git-and-github/)

To collaborate by sharing your code suggestions, you will need to "fork" our public repository.
For the basics of understanding forking and how to manage that fork, see: [https://help.github.com/articles/fork-a-repo](https://help.github.com/articles/fork-a-repo)

If you're looking for paid training courses on using git/github, see: [https://training.github.com/](https://training.github.com/)

Glossary of common terms in git and github: [https://help.github.com/articles/github-glossary](https://help.github.com/articles/github-glossary)



## Client Applications to Interact with git

To interact with git, you can use the command line or you can use a desktop application. (There are also mobile/tablet apps, but we won't cover that here.)

We recommend working with one of the following first two options.

* command line. Purists will use the command line, for reasons they will pine eloquently about if asked. There are hundreds of resources online showing how to use all the git features via command line, starting with the links at the top of this page.

* [SourceTree](http://www.sourcetreeapp.com/) for Windows and Mac - this is another good free desktop application which does a good job of giving you access to all the power of git/github/bitbucket/mercurial in an easy visual interface. We highly recommend using SourceTree due to its simplicity.

    When you first set up SourceTree, it will ask you to log in to your Atlassian account. The account is free, and no side-effects, and no personal information needs to be provided  besides name+email.

* There's another option, Github's own application: Github Desktop for [Windows](https://windows.github.com/) or [Mac](https://mac.github.com/).

    We're intentionally not documenting how to use Github Desktop, because [the Github Desktop documentation](https://docs.github.com/en/desktop) covers it well.

* While you won't find us documenting how to use them, there are several [other git GUI client apps](http://git-scm.com/downloads/guis)



## Workflow

Here's the workflow you'll want to use as a collaborator with Zen Cart&reg; and probably most other open source projects:

### CLA - Contributor License Agreement

By contributing code, you are agreeing that you willingly offer your contributions for use without compensation or restriction and that your contributions are entirely yours and not copyrighted or licensed by someone else under restrictive rules.


### Basic setup
 1. github account
  * Create a github account at [www.github.com](http://www.github.com)
 2. Fork the Repository
  * On the github site, [fork the project's repository](https://help.github.com/articles/fork-a-repo) (the main Zen Cart repository is at [https://github.com/zencart/zencart](https://github.com/zencart/zencart)).  Forking makes a copy of that repository into your own github account, which is where you will upload your changes since you only have "write" permissions in your own repository.
 3. Clone the repository to your own computer. (see below)

### Cloning a repository
* Get the URL for the repository you're cloning
 1. Go to **your** github account page
 2. Go to **your** fork of the Zen Cart repository: `https://github.com/YOURNAMEHERE/zencart`
 3. There's a green "Code" button, which if you click it, will show you the URL for cloning your repository. Click the clipboard icon to copy that URL to your computer's clipboard.

Now switch to your desktop application of choice and use that URL to clone the repository locally:

* command line: 
 1. pick a working directory on your PC
 2. cd into that directory
 3. type: `git clone PASTE-THAT-URL-HERE .` (note the `.` at the end, which says "put it in the current directory")

* [SourceTree](http://www.sourcetreeapp.com/):
 1. Choose File, New Clone...
 2. In the Source Path/URL, paste the URL you copied from github
 3. For the destination path, pick a folder on your PC
 4. For the bookmark name, call it whatever friendly name you want to remember this repo by. It will show up in [SourceTree](http://www.sourcetreeapp.com/)'s bookmarks list of repositories you've got.
 5. Click Clone or OK to have it start the clone. It will take a few seconds for it to download the repository contents to your computer.
	
### Add an upstream remote for keeping things up-to-date

To keep your own fork up-to-date, you'll need to periodically merge updates from the main Zen Cart repository. This involves telling your own local (on your PC) git repository about the main Zen Cart repository location. To do this you must add what's called an "upstream remote". (See the glossary link above for what a "remote" is.)

* command line:
 1. cd into the directory of the repository you're adding the remote to
 2. type: `git remote add upstream https://github.com/zencart/zencart.git`
 3. type: `git fetch upstream`

* [SourceTree](http://www.sourcetreeapp.com/):
 1. Choose Repositories from the main menu
 2. Choose Repository Settings...
 3. Click Add
 4. For Remote Name, use: **upstream**
 5. For the URL use: `https://github.com/zencart/zencart.git`
 6. For the github username, enter your own github account name
 7. Click OK
 8. Click Fetch
 
### Making a working-branch for each new Pull Request or feature you're working on
Any time you're going to contribute code changes, you'll want to first make a working branch. (For more on branches, see the glossary and other git references at the top of this page.) Branches are how git keeps different versions of changes separate from each other until such time as someone approves merging them together into the main branch.

##### Pick a branch name

 Decide on a new branch name. (The branch name should be brief, but meaningful; ideally a max of 6 words, all hyphenated, no spaces.)

##### Make the branch

 Now use that name for name-of-your-branch-here, below:

* command line:
 1. cd into the directory of the repository you're intending to make changes to
 2. In this example we'll be branching from the master branch
 3. Type: `git branch name-of-your-new-branch-here master`
 4. Type: `git checkout name-of-your-new-branch-here`
      
* [SourceTree](http://www.sourcetreeapp.com/):
 1. First, make sure you're in "History View"  (View, History View)
 2. Find where it shows `upstream/master`, and right-click on that row. Choose Branch... from the pop-up menu
 3. Give it the new branch name
 4. Leave the "checkout new branch" box checked
 5. Click Create Branch or OK

### Make your code changes

* Edit or create whatever files are applicable to the changes you wish to submit for consideration.
* Test your code. Test to make sure your changes work, and that you've not broken anything else in the process.
* Once your code is ready for submission, you'll need to commit the changes, and push them to your github account and then create a Pull Request. Those steps are described below.
* MAKE SURE YOUR CODE COMPLIES WITH ZEN CART CODING STANDARDS, else it may be rejected.
* If your code can be tested with phpunit, be sure to include those tests in your commits and pull request.


### Commits

To commit your code, you must first "stage" the files which are to be included. See the git docs mentioned at the top of this page for more detailed explanation of what this means.

Once you've staged the files, then you commit them, which saves that group of changes together.

You can make multiple commits (that is, stage the files and commit them) towards any given issue. This allows you to make numerous smaller commits which are easily described in connection with the specific files that relate to those smaller changes.

 * command line:

  1. cd into the directory of the repository you're committing from
  2. type `git status`
  3. this will give you a list of changed/added/deleted files
  4. type: `git add filename1.php filename2.php` (and any other files, etc)
  5. type: `git commit`
  6. This will pop up your text editor where you can supply a commit message. See explanation of commit messages in the sub section below.
  7. Save the message using whatever method your text editor uses to save-and-exit
  8. This will have the commit saved locally. You can continue working and making more commits until you're ready to push them all up to github (see pushing commits below)

 * [SourceTree](http://www.sourcetreeapp.com/):

  1. First, go into File Status view. Click on "Working Copy" in the left nav menu under File Status. Or, use the View menu and choose File Status View.
  2. Here you'll see a list of files on-screen which have changed in some way (edits, adds, deletes)
  3. You can also see exactly what's changed by clicking on those files and viewing the "diff" on the other side of the screen.
  4. For each file that you wish to include in the current commit, highlight it in the bottom part of the window, and click the Stage Selected button on the button-bar. It may ask you to confirm that you wish to Add it. (The Windows version has a tiny up-arrow that lets you do the staging as well, instead of using the Add from the top button-bar).
  5. Once your files are all staged, click the Commit button in the button bar
  6. This will open a dialog where you can supply a commit message. See the guidance around commit messages in the next section below.
  7. Click the commit button in the bottom right.
  8. Your commit is now saved locally on your PC. You can continue making more commits until you're ready to push them all to github, as described below.


### ABOUT COMMIT MESSAGES

1. The "subject" or "first line" of a commit message should be no more than 50 characters. 
2. The next lines can have as much detail as you like. Consider using [Github Markdown syntax](https://help.github.com/articles/github-flavored-markdown) for any formatting you might wish to include in the message. Feel free to use blank lines, and even use hyphens to create bulleted lists (hyphen plus a space)
3. If you're contributing code to help with an "Issue" that's already listed on the [Zen Cart github Issues](https://github.com/zencart/zencart/issues?state=open) page, include that issue number in your commit message, with the hashtag in front of it, like this: #101 for issue number 101.
4. Further to the point above, if your commit ["fixes" or "closes" or "resolves" an existing open issue then include the word "Fixes" before the issue number](https://help.github.com/articles/closing-issues-via-commit-messages/), ie: "Fixes #101" somewhere in your commit message. This will cause Github to close the "issue" ticket when your pull request is merged, and helps keep things tidy.
5. If you're committing code that addresses a bug reported on the Zen Cart support forum, include the URL for that bug from the forum, so we can cross-reference it.

Suggested reading: [7 Principles for Good Commit Messages](http://chris.beams.io/posts/git-commit/#seven-rules)


### Pushing Commits To Github

Now that you've made some commits to git on your local PC, you must push them to (your account on) github in order to prepare to share them.

 * command line:

  1. again, cd into the directory of your working repository
  2. type `git push origin name-of-my-working-branch`

 * [SourceTree](http://www.sourcetreeapp.com/):

  1. Click the Push button in the top button bar.
  2. From the pulldown for "Push to repository", be sure that "origin" is selected. That's **your** github repository, and you must push to there.
  3. Next make sure you check the box next to the branch you've been making your commits in. Uncheck all the others. 
  4. Click OK
  5. That's it! Now all the commits you've made in that branch on your PC will show up in your Github account.

### Pull Request

(You'll also see `Pull Request` referred to as a `PR`)

After you've pushed your working branch (ie: containing your new commits) to your own Github account, you will need to create a [Pull Request](https://help.github.com/articles/using-pull-requests/) in order to ask the Zen Cart committers to review it and consider it for inclusion in core code.

You'll do this from your browser:

1. Go to your Github account in your browser.
2. Go to *your* zencart repository.
3. You will see a green "Compare and Pull Request" button. Click it. (If it's been several hours since you did the push, it might not show the green bar. In that case, click the 'Branches' link, where you will see a Pull Request button next to each of your branches. Click the one next to the branch you want to do the pull request from.)
4. Now you can review the collection of commits and file changes, and add a descriptive message to the pull request. If you're fixing something that's already got an open issue for it, be sure that the issue number is included in your Pull Request message. ie: #101. If you believe your Pull Request fully fixes the open issue, then say "Fixes #101", as the keyword "Fixes" helps do proper cleanup of tickets once closed.
5. TIP: Generally your compare should be against `zencart:master`.  If you are contributing to a patch release, be sure that your pull request "compare" is indeed being compared against the `zencart:name-of-release` branch.  
6. Click the next green button to Create Pull Request
7. Now you [wait for others to review your code](https://github.com/thoughtbot/guides/tree/master/code-review). The Zen Cart team (and anyone else who has clicked "Watch" on the Zen Cart main repository) will get an alert about the pull request. Anyone wishing to reply with their opinions of what you've submitted can engage in dialog with you and one another while the code is reviewed. 
8. If your code hasn't complied with the coding standards, or has bugs or is incomplete, you may be asked to submit more commits to rectify the problems. In that case, you will repeat the steps above for making code changes, making commits, and pushing those commits to github. As long as you push to the same branch on github, then all those commits will automatically be included in the pull request, so reviewers can see the updates you push.
9. Once the core team decides what to do with it, they have basically three options: to accept it (merge the pull request) or defer it (until a later date) or reject it (not merge it and close the pull request). Github will automatically email you about all updates and comments made about your Pull Request.  (**NOTE:** Your PR won't be merged until you have signed the CLA.)

### Keeping Your Local Branch Current

When you or others make pull requests that are accepted into the Zen Cart core repository, that will make your own local copy be outdated. To keep current, you must periodically bring in the changes from the "upstream remote" we created earlier.  (see: https://help.github.com/articles/syncing-a-fork/)

* command line:
 1. type: `git fetch upstream`
 2. type: `git checkout master` (ie: if you're going to pull changes from the `master` branch)
 3. type: `git merge upstream/master` (merges your local copy with the upstream remote)
 4. type: `git push` (brings your forked repository up-to-date)

* [SourceTree](http://www.sourcetreeapp.com/):
 1. Click the Pull button in the top button bar
 2. For Pull From Repository, choose "upstream" from the pulldown menu
 3. For Remote Branch To Pull, choose "master"
 4. Leave the "commit merged changes immediately" box checked, and the others unchecked.
 5. Click OK

### Cleaning up old branches, or grabbing new branches
From time to time you and others will add or remove branches from the github repositories, and you will want to keep your PC in sync with those.

* command line:
 1. type: `git fetch upstream`
 
* [SourceTree](http://www.sourcetreeapp.com/):
 1. Click the Fetch button on the button bar
 2. There are 3 checkboxes. Check them all. (You could opt to not prune/delete any local branches you've created, if you want to preserve them to understand your own work history, by unchecking the corresponding box.)
(You could also fetch from individual remotes manually, and prune only when fetching from upstream, but never prune when fetching from your own github master) 
 3. Click OK

## References

There are many more great resources explaining how all of this works. Some which you might wish to review include:

* [git protocol by thoughtbot](https://github.com/thoughtbot/guides/tree/master/git)
* [code review process](https://github.com/thoughtbot/guides/tree/master/code-review)



---

&copy; 2014-2022 Zen Cart&reg; Creative Commons 3.0

*The SourceTree name is copyright Atlassian. Zen Cart receives no compensation or consideration for recommending SourceTree; we simply find it to be an extremely capable and useful app for beginners and experienced developers alike.* 
