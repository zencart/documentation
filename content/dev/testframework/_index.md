---
title: Test Framework
description: Using the automated tests
weight: 300
layout: docs
---

The Test Framework resides within the `not_for_release/testFramework` directory. This directory is only really available
if you `checkout` the Zen Cart code using git. It is not available if you just download the Zen Cart code via a
`release` link.

Running Zen Cart tests locally has the potential to **override your Zen Cart database and destroy data.**

FIXME - work in progress

## Preparation / Initial Setup

To prepare to run the Unit Test test suite:

1. First, install Composer:

* go to `getcomposer.org`
* download and install
* follow the Getting Started instructions.

2. Run `composer install`

3. Add `vendor/bin` to your path.

## Unit Tests

Unit tests can be run using

```
composer unit-tests
```

in the root directory of your Zen Cart install.

Currently, there are no local configuration requirements needed to run unit tests.
