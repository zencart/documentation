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

For this we use a Php script to automate this process.

The script is available in the https://github.com/zencart/versionstamper repository.

This is a private repository, so you may need to request access.

You need to create a feature branch in your Zen Cart directory for the version stamping changes, e.g.

`git checkout -b version-stamping-v158-alpha`


# Installing

Clone the [https://github.com/zencart/versionstamper](https://github.com/zencart/versionstamper) repository to your local computer.

Follow the instructions in the README. 

## config file

```$opts = [
'newVersion'    => 'v1.5.8-alpha', // note at this point we don't have to have a tag
'commitDate'    => '2022', //the date that will be used for the updatecommit
'copyrightDate' => '2022', //the date that will be used for the copyright date
'firstHash'     => 'c80dc0f2f88e3d461fca826a0a42aa5567a9dfcc', // usually the hash of tagged prior release
'lastHash'      => '81782eb678d072952ad919629e0352c77a49aaba', // usually the hash of the last commit for this new release
'ignoreDirectories' => ['includes/classes/vendors', '.circleci', '.github', 'laravel'],
'rootPath'      => '/home/wilt/Projects/zencart/'
];
```

+ newVersion - the version name of the release being worked on e.g. v1.5.8-alpha
+ commitDate - the year to use for updating the commit date - will be deprecated for auto setting
+ copyrightDate - the tear to use for the copyright date  - will be deprecated for auto setting
+ firstHash - the hash of the first commit in this branch - see below
+ lastHash - the hash of the first commit in this branch - see below
+ ignoreDirectories - a list of directories to ignore for changes
+ rootPath - the absolute path to your Zen Cart checkout

### firstHash

The `firstHash` represents the point which the release being worked on was branched from `master`
This can sometimes be difficult to find manually.

We can do something like
`git rev-list --ancestry-path $(git merge-base main v158)..v158 | tail -1`
replacing `v158` with the version we are working on

@FIXME need better instructions for getting first hash.


note: this assumes all versions prior were merged into master, and while the above is using a branch name, we may need to use a tag name
where there are multiple releases within a branch.

### lastHash

This is the hash of the last commit to the branch we are working on.
Can be found by looking at the github commits for our branch

### rootPath 

Be sure to update rootpath to the PATH to your local git folder.

## executing version stamper

`php versionstamp.php app:version-stamp`

This will run the version stamper in debug mode>
e.g. It will output information about the changes it would make, without altering any files.

We could also do
`php versionstamp.php app:version-stamp > somefile.txt`

to create a log of proposed changes that we could review

To actually make changes we would use

`php versionstamp.php app:version-stamp --mode=run`

**Remember that we should create a feature branch to encapsulate these changes, rather
than running directly against our working branch.**

Once the version stamping is complete, you will need to go to your Zen Cart checkout and 
commit and merge the changes created by the version stamping

There is a section of these docs called [Release Notes]({{< ref "release_notes" >}} "release notes"), in which you should capture some
basic information about the release progress.
