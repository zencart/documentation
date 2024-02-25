---
title: Version Stamping
weight: 40
layout: docs
category: release_process
---
Version stamping consists of a number of processes that are actioned on files that have 
changed in the release.

Those actions are 

 + Update the copyright year in the header of the fie to the current year.
 + Add/Update the details of what release the file was added/modified
 + Create a list of files that were added/deleted or modified and sort into those sections.

We use a php script to automate this process.

The script is available in the https://github.com/zencart/versionstamper repository.

This is a private repository for team members only.

## Preparatory Actions for Version Stamping 

1. Create a feature branch in your Zen Cart directory for the version stamping changes, e.g.

`git checkout -b version-stamping-v200`


## Installing the Version Stamper

Clone the [https://github.com/zencart/versionstamper](https://github.com/zencart/versionstamper) repository to your local computer.

Follow the instructions in the README. 

### config file

```$opts = [
    'prevOfficialRelease' => 'v1.5.7d',
    'newVersion' => 'v1.5.8', // note at this point we don't have to have a tag
    'prevStampedVersion' => 'v1.5.8', // note at this point we don't have to have a tag
    'commitDate' => '2022', //the date that will be used for the updatecommit
    'copyrightDate' => '2022', //the date that will be used for the copyright date
    'firstHash' => '28b79ce2120771411d08ef2c7cce5058e42a2cc3', // usually the hash of tagged prior release
    'lastHash' => '3bb5429b64095b89c671aae8f3e31cc9163b86b9', // usually the hash of the last commit for this new release
    'ignoreDirectories' => ['includes/classes/vendors', '.circleci', '.github', 'laravel', 'not_for_release'],
    'rootPath' => '/home/wilt/Projects/zencart/',
    'authorMap' => ['Chris Brown' => 'DrByte', 'Ian Wilson' => 'Zcwilt', 'zcwilt' => 'Zcwilt']
];

```

+ prevOfficialRelease The most recent official release e.g. v1.5.7d
+ prevStampedVersion The name of the most recent release that was version stamped (may have been a pre-release)
+ newVersion - the version name of the release being worked on e.g. v1.5.8
+ commitDate - the year to use for updating the commit date - will be deprecated for auto setting
+ copyrightDate - the tear to use for the copyright date  - will be deprecated for auto setting
+ firstHash - the hash of the first commit in this branch - see below
+ lastHash - the hash of the first commit in this branch - see below
+ ignoreDirectories - a list of directories to ignore for changes
+ rootPath - the absolute path to your Zen Cart checkout

#### firstHash

The `firstHash` represents the first commit after a previous tag/branch was created.
It also should represent the first commit after the last known version stamping commit was created.
This can sometimes be difficult to find manually.  See section below. 

#### lastHash

This is the hash of the last commit to the branch we are working on.  See section below.

#### rootPath 

Be sure to update rootpath to the PATH to your local git folder.

#### newVersion 

It is critically important that the spelling of this new version number is exactly what you want to use; it cannot be changed once the version stamper has been run. 


## Determining the Values of firstHash and lastHash
To help with finding both the first/last hash, we have a command line option within the version stamp code: 

`php versionstamp.php app:hash-suggest`

This command will output something like:

```
last Hash = 3bb5429b64095b89c671aae8f3e31cc9163b86b9
first Hash = 28b79ce2120771411d08ef2c7cce5058e42a2cc3
```

The output values can then be used to update the `config.php` file.

**Note:** Be sure the `prevStampedVersion` setting in the `config.php` file is correct prior to running this command.  You can find the exact spelling of the prior version by looking at the [releases page](https://github.com/zencart/zencart/releases). 


## Executing the Version Stamper

**Remember that we should have created a feature branch in our Zen Cart folder to encapsulate these changes, rather
than running directly against our working branch.**

If you run `git status` in your Zen Cart folder, you should see something like, 

```
On branch version-stamping-v200
nothing to commit, working tree clean
```

Back in your version stamper folder, run the stamper in debug mode first.

`php versionstamp.php app:version-stamp`

This will run the version stamper in debug mode 
i.e. It will output information about the changes it would make, without altering any files.

We could also do
`php versionstamp.php app:version-stamp > somefile.txt`

to create a log of proposed changes that we could review.


To actually make changes we would use

`php versionstamp.php app:version-stamp --mode=run`

Once the version stamping is complete, you will need to go to your Zen Cart folder and 
commit and merge the changes created by the version stamping.
Remember you will have to bypass merge protections since the branch has been locked for merges.

```
git add .
git commit 
git push 
-- Merge this change
git checkout master
-- update your branch
```

## Capturing information in Release Log

There is a section of these docs called [Release Log]({{< ref "release_log" >}} "release log"), in which you should capture some
basic information about the release progress.  Update `/dev/release_process/release_log.md`.


<div style="text-align:right;" id="next">
   <a class="btn btn-lg btn-primary mr-3 mb-4" href="/dev/release_process/release_tagging/">
        Next - Release Tagging<i class="fas fa-arrow-alt-circle-right ml-2"></i>
   </a>
</div>


