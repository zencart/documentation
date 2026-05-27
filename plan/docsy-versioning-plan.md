# Docsy Versioning And Dev Docs Plan

## Status

This document started as a proposal. It now also serves as a running status document.

Current state:

- the `content/dev` reorganization has been substantially implemented
- old developer-doc URLs are being preserved with aliases
- Docsy version-menu deployment has not been implemented yet

What remains is mostly:

- final polish on `content/dev`
- decisions about release-branch publication
- actual Docsy version-selector rollout

## Goal

Add Docsy version navigation to `zencart-docs` in a way that matches the current repository and deployment model, without restructuring the content tree around release versions.

The key decision is:

- keep `content/dev` and `content/user` as audience-based sections
- version the docs by branch and deployed site
- use Docsy's version menu only as navigation between published doc versions

## Current State

The current repository is already set up as a single Hugo site using Docsy:

- Docsy theme is configured in `config.toml`
- Netlify deploys the built site
- the primary public URL is `https://docs.zen-cart.com`

The config already contains:

```toml
version_menu = "Releases"
```

That means the theme is ready to show a version selector, but the selector will not appear until `[[params.versions]]` entries are added.

For the developer-doc tree specifically, the current implemented top-level structure is now:

```text
content/dev/
  _index.md
  admin/
  architecture/
  code/
  contributing/
  database/
    schema-history/
  getting-started/
  languages/
    legacy/
  modules/
  php/
  plugins/
    encapsulated/
  release/
  storefront/
  testing/
```

`content/dev/code/` is now transitional only.

## Why This Approach

Docsy's version menu is a link list, not a full version-management system.

It does not:

- automatically map one page to the equivalent page in another version
- manage content divergence inside one repository tree
- provide release-aware content resolution

Because of that, the cleanest model for `zencart-docs` is:

- one docs build per maintained release line
- one URL per published release line
- one shared version menu that links between those published sites

This keeps versioning simple and avoids duplicating `content/dev` and `content/user` into release-specific folders.

## Recommended Version Model

Use release branches and separate published doc sites.

Recommended branches:

- `main` or `current` for the current stable release
- `release/2.2`
- `release/2.1`
- optional `dev` for unreleased documentation

Recommended URLs:

- `https://docs.zen-cart.com/` for current stable
- `https://docs.zen-cart.com/2.2/`
- `https://docs.zen-cart.com/2.1/`
- `https://docs.zen-cart.com/dev/` for unreleased docs if published

## Content Structure Policy

Do not version the docs by creating content trees such as:

```text
content/
  current/
  2.2/
  2.1/
```

Do not repurpose `content/dev` to mean a release version.

Instead:

- keep `content/dev` for developer documentation
- keep `content/user` for user documentation
- let Git branches carry the release-specific differences

This preserves the current information architecture and avoids unnecessary duplication.

## Configuration Changes

Each published branch should define the full version menu in `config.toml`.

Example:

```toml
[params]
version_menu = "Releases"

[[params.versions]]
version = "Current"
url = "https://docs.zen-cart.com/"

[[params.versions]]
version = "2.2"
url = "https://docs.zen-cart.com/2.2/"

[[params.versions]]
version = "2.1"
url = "https://docs.zen-cart.com/2.1/"

[[params.versions]]
version = "Dev"
url = "https://docs.zen-cart.com/dev/"
```

Use absolute URLs. Since each version is a separate Hugo build, relative links in the version selector are the wrong tool.

## Base URL Rules

Each deployed version must build with the correct `baseURL`.

Examples:

- current stable:

```toml
baseURL = "https://docs.zen-cart.com/"
```

- 2.2 branch:

```toml
baseURL = "https://docs.zen-cart.com/2.2/"
```

- 2.1 branch:

```toml
baseURL = "https://docs.zen-cart.com/2.1/"
```

This matters because Hugo-generated links and assets depend on the correct base URL, especially when a site is published under a subpath.

## Netlify Deployment Model

The current repository uses Netlify for deployment.

The simplest production setup is:

- one Netlify site per maintained release line
- each Netlify site tracks one Git branch
- each site publishes to its assigned release URL

Suggested site mapping:

- `zencartdocs-current` -> `main` -> `https://docs.zen-cart.com/`
- `zencartdocs-2-2` -> `release/2.2` -> `https://docs.zen-cart.com/2.2/`
- `zencartdocs-2-1` -> `release/2.1` -> `https://docs.zen-cart.com/2.1/`
- optional `zencartdocs-dev` -> `dev` -> `https://docs.zen-cart.com/dev/`

This is easier to operate than trying to make one Netlify site publish multiple branches into multiple subdirectories.

## netlify.toml Considerations

The current build command is tied to the root URL.

Example current pattern:

```toml
command = "hugo -b https://docs.zen-cart.com"
```

For each release site, the build command or environment should match the actual published path.

Examples:

- current:

```toml
command = "hugo -b https://docs.zen-cart.com/"
```

- 2.2:

```toml
command = "hugo -b https://docs.zen-cart.com/2.2/"
```

- 2.1:

```toml
command = "hugo -b https://docs.zen-cart.com/2.1/"
```

This can be handled either by per-site Netlify configuration or by branch-specific config.

## Branch Policy

Recommended branch policy:

- `main`: current stable documentation
- `release/x.y`: maintained older release documentation
- `dev`: unreleased features only

Recommended content flow:

- update `main` first when content applies to current stable
- backport to `release/x.y` only if the change is still accurate for that release
- write unreleased feature docs only in `dev`

Avoid trying to keep all branches identical. That defeats the point of release versioning.

## Authoring Rules

Document these rules in `CONTRIBUTING.md`:

- contributors should choose the branch that matches the release they are documenting
- current release work goes to `main`
- maintenance corrections for older supported versions go to the relevant `release/x.y` branch
- unreleased features go to `dev`
- only backport content when it is still correct in that release line

This reduces accidental documentation drift and prevents current docs from being polluted with old-version caveats.

## Version Notices in the UI

Each published branch should display a short version-status notice.

Recommended notices:

- current stable: “You are viewing the current stable documentation.”
- maintained older release: “You are viewing documentation for Zen Cart 2.2. Some content may differ from current.”
- dev: “You are viewing unreleased development documentation.”

This can be implemented with a small branch-specific banner or partial.

The purpose is to reduce confusion for users who land from search engines or old links.

## Legacy Content Policy

`old_content/` should not be treated as the primary versioning mechanism.

Instead:

- keep it unpublished or lightly linked if it is strictly archival
- or move truly useful historical material into explicit archived release sites

The main navigation should focus on maintained documentation, not raw legacy content.

## Rollout Plan

### Phase 1: Minimal Viable Versioning

Implement only:

- `main` at `https://docs.zen-cart.com/`
- `release/2.2` at `https://docs.zen-cart.com/2.2/`
- `[[params.versions]]` entries in both

This gives working version navigation with minimal operational change.

### Phase 2: Older Maintained Release

If still needed, add:

- `release/2.1`
- its corresponding Netlify site
- a `2.1` version entry in all version menus

### Phase 3: Dev Docs

Add `dev` only if there is a clear need to publish unreleased developer or user documentation.

If there is no real audience for public prerelease docs, skip this phase.

### Phase 4: Cleanup and Policy

After versioning is working:

- update `CONTRIBUTING.md`
- add version-status banners
- review `old_content/`
- review hardcoded root-relative links that may behave differently under subpaths

## Local Verification Checklist

Before enabling production deployment for a versioned branch, verify locally:

```bash
hugo server
```

For a versioned subpath build, also test with an explicit base URL:

```bash
hugo server --baseURL http://localhost:1313/2.2/
```

Check the following:

- the Docsy version selector appears
- links resolve correctly under a subpath
- CSS and JS assets load correctly
- search still works as expected
- no hardcoded root links break navigation

## Recommended First Versioning Implementation

The best first versioning step is intentionally narrow:

- create `release/2.2`
- add `[[params.versions]]` to `config.toml`
- configure a second Netlify deployment for `/2.2/`

Now that the `content/dev` structure has already been reorganized, the versioning work can proceed independently of that IA cleanup.

## Summary

For `zencart-docs`, the right model is:

- audience-based content sections
- branch-based versioning
- separate deployments per maintained release line
- Docsy version selector as cross-site navigation

This matches how Docsy actually works and fits the current Netlify-based deployment model with minimal disruption.

## Appendix: `content/dev` Reorganization Plan

The versioning plan above intentionally keeps release management separate from information architecture. Versioning should be branch-based, while the `content/dev` tree should remain organized by developer needs rather than release lines.

This appendix now distinguishes between:

- original reorganization goals
- work already implemented
- remaining `content/dev` follow-up work

### Problem Statement

The current `content/dev` layout mixes several different organizing principles:

- audience areas
- architectural topics
- implementation how-to material
- release and contribution process docs
- historical and version-specific technical notes

The main structural problem is that `content/dev/code/` is acting as a catch-all bucket. It currently contains core architecture, admin topics, PHP guidance, database how-to material, notifier docs, forms, template topics, and module-related notes.

There are also a few more specific issues:

- `admin/` is too thin relative to the amount of admin-specific material living under `code/`
- `database/` and `schema/` are closely related but separated in a way that is not obvious to readers
- `testframework/` is accurate internally but less discoverable than `testing/`
- `release_process/` is process material, not technical reference material
- `plugins/encapsulated_plugins/` is more verbose than needed
- `code/Modules/` is capitalized inconsistently
- language-file docs appear to be split conceptually between `code/` and `languages/`

### Reorganization Principle

Keep the top-level `dev` docs organized by how developers look for information, not by where the legacy docs happened to accumulate.

The target buckets should answer questions like:

- “I need to understand the application internals.”
- “I need to build or extend an admin feature.”
- “I need database guidance.”
- “I need plugin guidance.”
- “I need PHP or framework-specific conventions.”
- “I need release or contribution process instructions.”

### Original Target Structure

```text
content/dev/
  _index.md
  getting-started/
  architecture/
  admin/
  storefront/
  plugins/
    legacy/
    encapsulated/
  database/
    schema-history/
  languages/
    legacy/
  frontend/
  php/
  testing/
  contributing/
  release/
```

This structure keeps audience-based grouping at the `dev` level, and then uses topic-based grouping within developer docs.

### Implemented So Far

The following reorganization work has already been completed:

- `developer_environment.md` moved to `getting-started/`
- core architecture topics moved from `code/` to `architecture/`
- admin topics moved from `code/` to `admin/`
- storefront topics moved from `code/` to `storefront/`
- PHP-focused topics moved from `code/` to `php/`
- database how-to docs moved from `code/` to `database/`
- `schema/` moved under `database/schema-history/`
- `testframework/` renamed to `testing/`
- `release_process/` renamed to `release/`
- `languages/pre_158/` renamed to `languages/legacy/`
- `plugins/encapsulated_plugins/` renamed to `plugins/encapsulated/`
- `code/Modules/` moved to `modules/`
- `code/view_builders/` moved to `admin/view-builders/`
- `libraries/` folded into `storefront/`
- `payment/` folded into `modules/`
- duplicate `code/158_*` stubs removed, with aliases retained through the real language pages
- `content/dev/*/_index.md` pages were expanded into real section landing pages
- many internal links were updated to the new canonical paths
- aliases were preserved so older `/dev/...` links still resolve

### What Each Section Means

#### `getting-started/`

Use this for orientation and local setup.

Likely content:

- developer environment setup
- how to navigate the docs set
- possibly high-level “where to start” pages for new contributors

#### `architecture/`

Use this for core Zen Cart internals and system behavior.

This is where developers should go when they want to understand how the platform works rather than how to do one specific task.

Likely moves from `code/`:

- program flow
- init system
- inclusion rules
- extra folders
- constants
- product types
- notifiers
- notifier report and notifier lists
- observer creation example

#### `admin/`

Use this for admin-specific developer topics.

This should absorb admin material currently buried in `code/`.

Likely moves:

- admin templating
- admin sanitization
- admin cron
- creating menu entries
- sorting menu entries
- reports
- widgets
- future view-builder material if that section grows

#### `storefront/`

Use this for storefront-facing implementation patterns.

Likely candidates:

- forms
- template settings
- displaying custom fields
- other page or rendering guidance that is not core architecture

This bucket may remain smaller than others, but it is still clearer than leaving storefront implementation topics inside `code/`.

#### `plugins/`

Keep plugin material together, but split it into clearer subgroups.

Suggested substructure:

```text
plugins/
  _index.md
  basics/
  governance/
  encapsulated/
  legacy/
```

Suggested use:

- `basics/`: adding config, language files, versions, basic plugin mechanics
- `governance/`: rules, adoption, help, GitHub process
- `encapsulated/`: encapsulated plugin architecture and implementation notes
- `legacy/`: older plugin-specific compatibility or migration material if needed

Also rename:

- `plugins/encapsulated_plugins/` -> `plugins/encapsulated/`

#### `database/`

Unify database and schema guidance under one obvious section.

Suggested substructure:

```text
database/
  _index.md
  querying/
  tables-and-fields/
  schema-history/
  examples/
```

Move here:

- database querying guidance
- creating tables
- add/modify field examples
- child table examples
- order status history update examples
- existing `database/*`
- all `schema/schema_*.md`
- schema renaming guidance

The reader should not need to decide between “database” and “schema” before finding the right docs.

#### `languages/`

Keep language-file material here as the single home for language docs.

Also consider renaming:

- `languages/pre_158/` -> `languages/legacy/`

If there are duplicate or overlapping language docs elsewhere, consolidate them here.

#### `storefront/`

This section now also absorbs the storefront-facing library docs that were previously under `libraries/`.

That means it includes:

- forms
- template settings
- custom field display guidance
- Bootstrap
- jQuery
- Font Awesome

#### `php/`

Use this for PHP-language and coding-style guidance rather than Zen Cart architecture.

Likely moves:

- PHP idioms
- PHP updates
- PHP version deprecations
- data validation if it reads more like language/runtime guidance than app behavior

#### `testing/`

This section is now implemented as `testing/`, with the old `testframework` path preserved by alias.

#### `contributing/`

This can remain, but should be framed explicitly as process and contribution guidance.

#### `release/`

This section is now implemented as `release/`, with the old `release_process` path preserved by alias.

### Remaining `content/dev` Work

The major tree work is done. Remaining work is now mostly polish and maintenance:

1. Continue reviewing page titles and descriptions for readability and consistency.
2. Continue normalizing metadata where older wording or inconsistent frontmatter remains.
3. Decide how visible the transitional `content/dev/code/_index.md` page should remain.
4. Decide whether `release_history.md` should move under `dev/release/`.
5. Continue checking canonical links as content evolves, while preserving aliases.
6. Periodically run local Hugo builds to verify that navigation and templates still behave correctly.

### Migration Strategy Used

The `content/dev` reorganization was effectively carried out in layered passes:

1. structural cleanup
2. section reframing
3. canonical-link cleanup
4. metadata and ordering cleanup
5. title/description readability cleanup

That sequence kept the risk lower than trying to redesign structure, wording, links, and metadata all at once.

### Relationship to the Versioning Plan

These two plans should be treated as complementary but separate:

- versioning decides how releases are published
- tree reorganization decides how developers navigate the docs within a release

Originally, the recommendation was:

1. get basic versioning working
2. then perform the `content/dev` reorganization

In practice, the `content/dev` reorganization was completed first.

That means the current practical order is now:

1. finish any remaining `content/dev` polish
2. then implement the Docsy versioning and deployment work

### Current Recommendation

For `content/dev`, the remaining work is no longer major tree movement.

The next priority should be:

- small polish passes
- navigation verification
- final canonical-link checks

For the broader plan, the next major implementation area is now the Docsy version selector and deployment strategy.
