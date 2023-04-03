---
title: Change Guidelines 
description: Details of submitting your PR 
weight: 2
---

## How do you make a change? 
Changes are made through pull requests ("PR's"). If you are unfamiliar with pull requests, please review the project's [Github Workflow](/dev/contributing/github_workflow/). 

## What should go into a change? 
For non-trivial changes, the best practice is to have a single PR for each issue you are addressing. The reasons for this include: 
* The repo maintainer may want to merge one change but not another for the stability of the build.
* A user may wish to see how to resolve a specific problem in their currently running cart, and wants to change the fewest things possible.
* A small self-contained (aka "canonical") changeset is easier to evaluate.

### How To Get My Changes Reviewed And Accepted?
[How To Make Your Code Reviewer Fall In Love With You](https://mtlynch.io/code-review-love/) should be required reading for everyone submitting code.

## Bug Fixes and Formatting 
When changing existing files, try not to make large formatting changes. 
Keeping the existing format allows people to more easily compare versions. 
See [Coding Standards](/dev/contributing/coding_standards/) for more details.

In cases where a significant amount of reformatting is necessary and approved by the dev team, that should be done as a standalone commit and PR, where NO functional changes are made. 
It should be formatting-only. Otherwise it becomes nearly impossible to find "who changed what when and why" when investigating code history at a later date.


## How should I document a change?
Documentation starts with the title of each commit and of the PR, and extends into the commit/PR descriptions.

A good title describes succinctly the issue being solved. The commit title shows up in commit history, and is very important when exploring historical changes when troubleshooting problems or reviewing history vs new PRs. The more succinct but expressive your commit title, the better.

By default the first line of a commit description also becomes the "title" of a PR.
Preferably the commit "title" should be under 50 characters. When subsequently submitting a PR with that commit the PR title could be expanded to longer (80-100 chars) if it makes the PR intent clearer.

**Good PR Title** 

_Check value of `foo` in account creation submission_

(Note that `Fix bug in account creation` and `Fixes #12345` would NOT be good PR titles.)

<hr>

In the body of the PR, explain the issue, contrasting the current behavior with the expected behavior.

**Good behavior description:**

* Current behavior: the person submitting the form can add non-alphanumeric data to the `foo` field; this is undesirable, since `foo` is only alphanumeric. 
* Desired behavior: entry of non-alphanumeric data displays an error message and causes the submission to fail.

Also, screenshots of before/after for any changes affecting UI will make the intention clearer and easier for reviewers to understand.

A mere link to a forum thread or issue number is not sufficient. See "linking related issues" below.

<hr>

Show your work!  Demonstrate how you tested the change you are submitting.

**Good Test Data:**
* Set the value of `foo` to `4323*(!`.  Observe that the submission fails and an error is shown.
* Set the value of `foo` to `good entry`.  Observe that no error is shown and the submission succeeds.

<hr>

**Special Case: Brand New files**

If you are adding a new file, please be sure to add the header so the version stamper can update the file on the next release.

```
/**
 * @copyright Copyright 2003-2023 Zen Cart Development Team
 * @license https://www.zen-cart.com/license/2_0.txt GNU Public License V2.0
 * @version $Id:   
 */
```

**Linking Related Issues**

Related Issues should be referenced using `#` followed by the issue number, ie: `#12345`.
If the PR fully resolves a related issue, prefix the issue number with `Fixes `, ie: `Fixes #12345` in order to link them up so the issue is automatically closed when the PR gets merged.

**NOTE:** Even if a topic is fully described in the related Issue, your description in the PR _should still include the details of what the PR is about_. Merely referencing the Issue Number is seldom ideal, particularly when the related issue has had many comments/discussion notes and therefore would require a future reader of the PR (including the person reviewing the code before merge) to go and re-read the entire discussion. Save them the trouble by providing a good description as explained above. That way the reviewer knows the landscape up-front; they can refer to the related Issue for additional clarity but shouldn't be forced to go there for it. (An occasional exception is if the issue has no comments/discussion and the best description would be merely a copy/paste; however, in that case it probably could have been a PR directly in the first place.)
