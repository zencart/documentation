---
title: Change Guidelines 
weight: 2
---

## How do you make a change? 
Changes are made through pull requests. If you are unfamiliar with pull requests, please review the project's [Github Workflow](/dev/contributing/github_workflow/). 

## What should go into a change? 
For non-trivial changes, the best practice is to have a single PR for each issue you are addressing. The reasons for this are as follows: 
* The repo maintainer may want to merge one change but not another for the stability of the build.
* A user may wish to see how to resolve a specific problem in their currently running cart, and wants to change the fewest things possible.  
* A small self-contained changeset is easier to evaluate.

## Bug Fixes and Formatting 
When changing existing files, try not to make large formatting changes.  Keeping the existing format allows people to more easily compare versions.  See 
[Coding Standards](/dev/contributing/coding_standards/) for more details. 

## How should I document a change?  
Documentation starts with the title of the PR.  A good title describes succinctly the issue being solved. 

**Good PR Title** 

_Check value of `foo` in account creation submission_

(Note that _Fix bug in account creation_ would not be a good PR title.)

<hr>

In the body of the PR, explain the issue, contrasting the current behavior
with the expected behavior. 

**Good behavior description:**

* Current behavior: the person submitting  the form can add non-alphanumeric data to the `foo` field; this is undesirable, since `foo` is only alphanumeric. 
* Desired behavior: entry of non-alphanumeric data displays an error message and causes the submission to fail.

<hr>

Show your work!  Demonstrate how you tested the change you are submitting.

**Good Test Data:**
* Set the value of `foo` to `4323*(!`.  Observe that the submission fails and an error is shown.
* Set the value of `foo` to `good entry`.  Observe that no error is shown and the submission succeeds.

