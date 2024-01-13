---
title: Versioning 
description: How Zen Cart Releases are Numbered
category: about_us
weight: 10
---

Note: This FAQ covers versioning of Zen Cart for release 2.0.0 and forward. 


Starting with release 2.0.0 (to be released in early 2024), the version numbering system used by Zen Cart has been changed to be more standards-based.

In this system, releases are numbered using [Semantic Versioning](https://semver.org/), also known as [PHP "standard"](https://www.php.net/manual/en/function.version-compare.php) versioning:

MAJOR.MINOR.PATCH

Major and Minor releases require attention to hosting capabilities and their impact on plugins or site-specific customizations.

Patch releases are about smaller bug-fixes applied to minor releases; they are smaller and do not contain database changes (so running `zc_install` is not required).

Read below for how to understand better what a version number may mean to you and your store.

----
## Factors considered by the Zen Cart team when bumping version numbers
Here is how we're applying the meaning of major and minor and patch terminologies.

Again, these are the criteria WE use to establish the next version number. This does NOT mean that "all" of these factors will always be present in a given release. Always consult the release-documentation to understand the impact any of the changes may have on your site or your hosting platform, etc.

### First-digit
Some or all of these criteria may be the reason for incrementing the First digit in the release number. But, a bump to this first-digit number does not necessarily mean that "all" of the following are affected by the release. (eg: if we drop support for an older PHP version it doesn't mean we've made huge changes to all the templates and language files, but we'll bump the major-version number because it's a significant factor)
- Significant dependency-changes for hosting platform (eg: dropped support for a still-prevalent PHP version or other parts of LAMP stack)
- Requires a new extension in PHP/Apache that's not commonly-installed by default
- Large-overhauls to existing features, or a significant number of files require attention in order to upgrade
- Addition of major new features/infrastructures
- DB Schema updates included, if needed
- Running zc_install is required, whether to inspect dependencies or to do db-updates
- Upgrade steps might be deemed "complicated", and the merging of changes may sometimes be tedious in some places
- Major changes/impact to templates
- Major impacts to site-specific customizations
- Major language-file changes
- Plugins/Addons may require major work to upgrade for compatibility


### Second-digit
- Noteworthy feature-additions / improvements
- Collection of numerous updates/fixes which aren't "major" in themselves, but warrants a release
- May be used to add support for a newer PHP/MySQL version if not a lot of files are impacted (or a Major version might be used if the number of affected files is significant or will impact plugins in big ways)
- Upgrade steps should not be deemed "super-complicated"
- Templates don't require significant restructuring (rearranging of sections of logic), so while there may be many changes they are easy to merge using a text-comparison utility
- May include DB Schema updates, if needed
- Upgrades will require running zc_install to check that DB updates for major/minor versions have been applied-to-date (whether schema updates were included or not)
- Plugins/Addons should not require major work to upgrade, but authors should review and test and assert compatibility.
- Might include addition of New modules, if a Major version isn't needed for other reasons
- Language files may include additions, but any splitting of constants into smaller segments should be minimal
- This digit will be most-commonly updated once per year
- Ideally will aim to do at least one of these releases per year
- If a release is "not major", and is "not merely a small bugfix/patch", then this "minor" digit will be incremented.


### Third-digit
- Bugfix emphasis
- Smaller collection of updates/fixes that don't touch a lot of files, and don't warrant a 2nd-digit bump
- This number might be bumped a couple times per year
- No DB Schema updates required
- Templates only affected insomuch as bugfixes might touch some template files
- Language files only affected if fixing a bug, no major replacements/swaps to language constants
- Plugins not intentionally affected, apart from how bugfixes might impact them because of files/features affected by the release.
- Upgrade impact: minor, as in changes should be easy to merge using a text-comparison utility


### Fourth-digit
- Rarely used (ie: almost **never**): merely for **very minor** patches.
- If used, might not be formally published (might merely be "tagged" on GitHub)
- Super-simple to upgrade by replacing a tiny number of `.php` files.
- Not expecting any impacts to plugins/addons/templates/customizations.



## How would past releases have been numbered under this system? 

**Hypothetically**, if this system had been adopted when Zen Cart 1.3.9 was replaced by 1.5.0, it might have rolled out like the following. (No, we're not renumbering those old versions! They are what they are.)

|Old Versioning | New Versioning | Reasoning |
|--------------------|-------------------|--------------------|
|1.5.0|2.0.0|Database now defaults to `utf8`, sanitization added, USPS shipping and `tell-a-friend` removed|
|1.5.1|2.1.0|Adds `/logs` handling, improved notification architecture, adds `querycache`|
|1.5.2|2.2.0|(This one was never formally released, so treating as a minor update in this chart.)|
|1.5.3|3.0.0|Adds support for PHP 5.4 and 5.6, now requires `mysqli` instead of `mysql`, requires minimum PHP 5.3|
|1.5.4|3.1.0|Adds AJAX infrastructure, requires minimum PHP 5.5|
|1.5.5|4.0.0|Added highly-requested new `responsive_classic` template, Adds support for PHP 7.1|
|1.5.5a|4.0.1|Fix zero-date issues for upgrade process, admin sanitization fixes for plugins|
|1.5.5b|4.0.2|Fix some Chrome browser issues, Fix admin-sanitizer bugs, fix shipping logic, payment module updates|
|1.5.5c|4.1.0|Fix an email security bug (3rd party), fix some PHP7 compatibility issues|
|1.5.5d|4.1.1|Fix another email security bug (3rd party), Fix an authorizenet storage problem|
|1.5.5e|4.1.2|Fix a bug created in v155c, remove need for Apache mod_compat to be present|
|1.5.5f|4.1.3 or 4.2.0|Several payment modules updated, Square support was added, db query cache-bypass added|
|1.5.6|5.0.0|Adds support for PHP 7.2 and 7.3, Bootstrap supported for admin pages, introduces `utf8mb4` DB_CHARSET|
|1.5.7|6.0.0|Adds support for PHP 7.4 and 8.0, adds `ask_a_question` page and `zc_plugins` support. Drops PHP 5.6 support|
|1.5.7a|6.0.1|Various bugfixes; samesite cookie feature added|
|1.5.7b|6.0.2|Bugfixes to admin changes added in 1.5.7; now remembers order-weight in order history|
|1.5.7c|6.0.3|Accessibility improvements, PHP 8.0 compatibility improvements|
|1.5.7d|6.1.0|PluginManager improvements, fix longstanding db query-factory bug |
|1.5.8|7.0.0|Adds support for PHP 8.1 and 8.2, restructures language handling, Requires PHP 7.3 minimum and MySQL 5.7.8 minimum (which is already commonplace).|
|1.5.8a|7.1.0|Adds support for "template init" scripts on a template change, templates can support single-column sideboxes, CKEditor updated.|

So, after 1.5.8a, instead of the next release being 1.5.9, we're bumping to 2.0.0 because it contains a major overhaul to FontAwesome icon naming which affects a lot of files in catalog and admin, and some admin files related to pre-158 admin menu system have been removed and therefore may affect plugins that formerly depended on those files but fixing those plugins should be very simple.



## Prior Versioning System

Before 2.0.0, Zen Cart used a versioning system in which three dotted numbers were used to indicate a major release, and an alphabetic character was appended to indicate a patch release. For example, 1.5.7 and 1.5.8 were major releases, whereas 1.5.7c and 1.5.8a are patch releases.  See [Release History](/user/about_us/release_history/). 

