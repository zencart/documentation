# Zen Cart Developer Docs

[![Netlify Status](https://api.netlify.com/api/v1/badges/4d957b89-ea0c-46dc-93a2-2204d5a1a2b9/deploy-status)](https://app.netlify.com/sites/zencartdocs/deploys)

Merged PRs to the Content area of this repo automatically deploy to https://docs.zen-cart.com

## Content

The core content of the generated docs comes from the `/content/dev` and `/content/user` folders. 

**Please do not make edits to other folders.**

The files are in Markdown format, but also include a brief YAML "header" using the following syntax:
```yaml
---
title: Page Title Goes Here
weight: 1
---
```

The `weight` parameter indicates sort order of display amongst files at the same folder level.

The repository is based on the [Docsy](https://www.docsy.dev/docs/) Documentation Template.


## Local Dev Testing

First ensure that Hugo is installed on your system. On a Mac, use homebrew:

```
brew install hugo
```

Note: you will need to have a recent version of Hugo.  If `hugo version` returns a value less than 0.53, should should update it (`brew upgrade hugo` on a Mac). 

Then do a submodule update in the folder where you checked out this project. 

```
git clone git@github.com:zencart/documentation.git zendocs
cd zendocs
git submodule update --init --recursive
```

Create and update files in the `content/dev` and `content/user` folders.  If you create a new folder under one of these folders, be sure to create an `_index.md` file, following the example from an existing folder. 

Now the site can be served locally with Hugo. During development, you can have Hugo spin up a local webserver and watch for changes.

```
cd zendocs
hugo server
```

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

### Security

If you discover any security related issues, please email security@zen-cart.com instead of using the issue tracker.


## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
