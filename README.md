# Zen Cart Developer Docs

[![Netlify Status](https://api.netlify.com/api/v1/badges/4d957b89-ea0c-46dc-93a2-2204d5a1a2b9/deploy-status)](https://app.netlify.com/sites/zencartdocs/deploys)

Merged PRs to the Content area of this repo automatically deploy to https://docs.zen-cart.com


## Contributing

Interesting in contributing to these docs? Please see [CONTRIBUTING](CONTRIBUTING.md) for details.


## Content

Create and update files in the `content/dev` and `content/user` folders, for developer and user documentation respectively.   

**Please do not make edits to other folders.**

The files are in Markdown format. Details on file structure and contents are provided in [CONTRIBUTING](CONTRIBUTING.md).


## Local Dev Testing

First ensure that Hugo (v0.53 or greater) is installed on your system. On a Mac, use Homebrew:

```
brew install hugo && brew upgrade hugo
```

Installing Hugo on Windows takes a few more steps; do a web search for the most current instructions. 

Once you have installed Hugo, fork this repository into your own github account, and then clone this project locally and do a submodule update to get all its dependencies:

```
git clone git@github.com:YOUR-GITHUB-USERNAME/documentation.git zendocs
cd zendocs
git submodule update --init --recursive
```

Now the site can be served locally with Hugo. During development, you can have Hugo spin up a local webserver and watch for changes.

```
cd zendocs
hugo server
```

The repository is based on the [Docsy](https://www.docsy.dev/docs/) Documentation Template, in case you need a reference for troubleshooting purposes.


### Security

If you discover any security related issues, please email security@zen-cart.com instead of using the issue tracker.


## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
