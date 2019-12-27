# Zen Cart Developer Docs

[![Netlify Status](https://api.netlify.com/api/v1/badges/4d957b89-ea0c-46dc-93a2-2204d5a1a2b9/deploy-status)](https://app.netlify.com/sites/zencartdocs/deploys)

Merged PRs to the Content area of this repo automatically deploy to https://docs.zen-cart.com

## Content

The core content of the generated docs comes from the `/content/dev` and `/content/user` folders. 

**Please do not make edits to other folders.**

The files are in Markdown format, but also include a brief "header", based on Hugo syntax.

The repository is based on the [Docsy](https://www.docsy.dev/docs/) Documentation Template.


## Local Dev Testing

First ensure that Hugo is installed on your system.

```
brew install hugo
```

Edit content in the Content folders.


Now the site can be built with Hugo. During development, you can have Hugo spin up a local webserver and watch for changes.

```
cd [directory where this repo is cloned]
hugo server
```

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

### Security

If you discover any security related issues, please email security@zen-cart.com instead of using the issue tracker.


## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
