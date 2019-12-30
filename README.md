# Zen Cart Developer Docs

[![Netlify Status](https://api.netlify.com/api/v1/badges/4d957b89-ea0c-46dc-93a2-2204d5a1a2b9/deploy-status)](https://app.netlify.com/sites/zencartdocs/deploys)

Merged PRs to the Content area of this repo automatically deploy to https://docs.zen-cart.com

## Content

Create and update files in the `content/dev` and `content/user` folders.  

**Please do not make edits to other folders.**

The files are in Markdown format, but also include a brief YAML "header" using the following syntax:
```yaml
---
title: Page Title Goes Here
weight: 1
---
```

The `weight` parameter indicates sort order of display amongst files at the same folder level.

If you create a new folder (such as for a category/topic), be sure to create an `_index.md` file, following the example from an existing folder. 


## Local Dev Testing

First ensure that Hugo (v0.53 or greater) is installed on your system. On a Mac, use homebrew:

```
brew install hugo && brew upgrade hugo
```

Then clone this project and do a submodule update to get all its dependencies:

```
git clone git@github.com:zencart/documentation.git zendocs
cd zendocs
git submodule update --init --recursive
```

Now the site can be served locally with Hugo. During development, you can have Hugo spin up a local webserver and watch for changes.

```
cd zendocs
hugo server
```

The repository is based on the [Docsy](https://www.docsy.dev/docs/) Documentation Template, in case you need a reference for troubleshooting purposes.


## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

### Security

If you discover any security related issues, please email security@zen-cart.com instead of using the issue tracker.


## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
