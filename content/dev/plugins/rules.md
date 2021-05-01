---
title: Rules for Plugins
description: How to build a plugin that will be accepted 
category: plugins
weight: 1
---
## What is a Contribution/Addon/Plugin?
The Open Source community has many great benefits. One such benefit is the ability for many people to collectively share their knowledge, creativity, and expertise by extending the capabilities of existing software products.  It's very common for someone to install a product such as Zen Cart and want to make some customizations unique to their business, and then share those changes by contributing back to the Zen Cart community for everyone's benefit.  Packaging up the new/changed files along with instructions on how to implement those onto another site is essentially what a contribution/addon comprises.

## Acceptable Contributions
Addon/Contribution/Plugin authors who wish to discuss and support their addon via the Zen Cart support site must post their contribution to the "Plugins" area of the Zen Cart support site.   Modules which are not in the Plugins area are not to be discussed on the Zen Cart support forum.

The Zen Cart Support Forum is the place to explore and create new ideas and features; it is not a venue for advertising and promotion. Paid/commercial addons will not be accepted for the Downloads section, and advertisements for such will not be allowed on the forum.

Contributions containing content which could be construed as objectionable or unsuited for general use are not acceptable and will thus be rejected.

## Addon/Contribution Requirements
Contributed Addons which are hosted in the Zen Cart "downloads" area must comply with the following standards:

* License: Must be GPL, since it's integrating into Zen Cart core code, which is GPL. A complete copy of the license should be included in the contribution files, preferably as a separate file. If an addon is free-standing (ie: doesn't use *any* existing Zen Cart files in order to operate) then it can be licensed under another license provided that license is fully compatible with GPL.

   You can find the GPL license details at:  http://www.gnu.org/licenses/licenses.html#GPL

* File Format: Contributions should be submitted in .ZIP format wherever possible for maximum compatibility to those who would download it (other compression formats are harder to use and less likely to have readily-available support for decompressing).

* File Size: The file should be as SMALL AS POSSIBLE. Excessively large graphics or PDF files should be avoided.

* Documentation: See "Documentation Requirements" below.

* Support: A support thread in the appropriate Addons/Contributions area of the Zen Cart support forum should be opened following activation of a submitted contribution, where free support for that addon will delivered by the author and the community at large. Support for the addon should take place on the Zen Cart forum.

### Plugin Contents: 

 * Documentation files (see "Documentation Requirements" below).
 * PHP files: The zipped distribution should contain a complete directory structure of files which should be added/edited/merged to effect implementation of the contribution.  The built-in override system should be used where possible.
 * jQuery: The default Zen Cart template includes automatic loading of jQuery from the jQuery CDN. Your plugin should NOT include the jQuery package. If it needs jQuery, it should expect that the store's template already loads jQuery. That said, you should ensure your plugin works with the latest version of jQuery available at the time of posting/updating your plugin. It would be beneficial to also note what versions of jQuery your plugin "requires" and "is compatible with", so storeowners have an idea what changes they may need to make or whether your plugin is compatible with the tech tools already on their site.
 * SQL files: If there are database changes required, an SQL file should be supplied containing any SQL commands which need to be run by the person installing the contribution.
An "uninstall" SQL script should be included as well so the end user can uninstall the SQL changes if they choose to remove the contribution.
 
   Any included .SQL files should be written without the use of database table-prefixes (such as `zen_`), since a default Zen Cart install doesn't use any such prefixes.
 
   **NOTE:** More advanced module writers may elect to have built-in SQL setup capability, as long as uninstall instructions/scripts are provided.

* Updates: If you are submitting an update to a contribution, please be sure to include the full set of files comprising that contribution. There should not be a need to install a prior version before installing your update. Each submission should be complete.

## Unacceptable Submissions
- It is *not* acceptable to submit crippled modules which are only teasers for paid services. ie:  a "limited" module with a sales pitch for a "full featured" commercial add-on is not permitted.
- Having "donate to me" buttons in the add-on, either admin-side or storefront-side or is not permitted. A single statement about where to send donations may be added to the documentation, but should be discrete and not plastered all over the place.
- Connectors to commercial services, such as embedded affiliate links or referral tracking links are not permitted.
- In the interest of protecting the end-user's privacy and identity, any sort of call-home capability is forbidden, whether disclosed or not.
- Obfuscating or encrypting (such as via ionCube, Zend Guard, etc.) is *not* acceptable.

## Documentation Requirements
1. Complete documentation for the contribution must be contained in the contribution's distribution zip file, preferably in a file named `README-addonnamehere.TXT` (or `README.md`). Using a URL shortcut/link to point to another website for readme and/or install/uninstall documentation is not acceptable.
1. The author should be acknowledged - and a single link to their site is acceptable, as is a tasteful request for donations. 
1. Prior authors/contributors should be acknowledged.
1. Documentation should include clear steps outlining what to do once the contribution has been unzipped, including where to put the unzipped files and how to do any database updates/changes.
1. Documentation should be written with the "newbie" in mind ... ie: Don't make assumptions that the person using the contribution has any more understanding than how to unzip the file. This helps address the lowest-common-denominator skill-set and helps minimize support questions which can cause frustration and time drain on the author to supply support.
1. Documentation should include uninstall instructions in case someone wants to cleanly remove the addon from their store ... without breaking normal operation or leaving old fragments/data behind.  This should address any files to be removed, any folders to be removed, any permissions changes to be undone, and any SQL changes/deletions applicable to the addon.

## Submission

New plugins should be submitted using the [Submit New Plugin form](https://www.zen-cart.com/downloads.php?do=add). 

Submissions will be reviewed for compliance and acceptability. Such reviews happen approximately once or twice weekly.  Contribution authors will be notified by email when their contribution has been activated.

Updates to existing contributions should be uploaded as <b>updates</b> to the existing contribution, and not as new contributions with merely a different version number.  To do this, find the plugin in the Plugins Library, and click the _Submit an Updated Version_ link below the orange Download button.  

When doing an update, it is appropriate to acknowledge prior work done by other contributors, including their copyright notices. Submitting an update for the purpose of rebranding with one's own credits is frowned upon. 

The Zen Cart team reserves the right at its own discretion to reject or deny any contribution and/or update, with or without notification, especially if it fails to comply with these published standards or if it risks being dangerous or confusing to those who might try to use it.

Submitting a contribution means you agree with the GPL and consent for your contribution to be used under the terms of the GPL.

