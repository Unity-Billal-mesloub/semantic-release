<h1 align="center" style="border-bottom: none;">📦🚀 semantic-release</h1>
<h3 align="center">Fully automated version management and package publishing</h3>
<p align="center">
  <a href="https://github.com/Unity-Billal-mesloub/semantic-release/discussions">
    <img alt="Join the community on GitHub Discussions" src="https://img.shields.io/badge/Join%20the%20community-on%20GitHub%20Discussions-blue">
  </a>
  <a href="https://github.com/Unity-Billal-mesloub/semantic-release/actions/workflows/test.yml">
    <img alt="Build states" src="https://github.com/Unity-Billal-mesloub/semantic-release/actions/workflows/test.yml/badge.svg">
  </a>
  <a href="https://securityscorecards.dev/viewer/?uri=github.com/Unity-Billal-mesloub/semantic-release">
    <img alt="OpenSSF Scorecard" src="https://api.securityscorecards.dev/projects/github.com/Unity-Billal-mesloub/semantic-release/badge">
  </a>
  <a href="#badge">
    <img alt="semantic-release: angular" src="https://img.shields.io/badge/semantic--release-angular-e10079?logo=semantic-release">
  </a>
</p>
<p align="center">
  <a href="https://www.npmjs.com/package/semantic-release">
    <img alt="npm latest version" src="https://img.shields.io/npm/v/semantic-release/latest.svg">
  </a>
  <a href="https://www.npmjs.com/package/semantic-release">
    <img alt="npm next version" src="https://img.shields.io/npm/v/semantic-release/next.svg">
  </a>
  <a href="https://www.npmjs.com/package/semantic-release">
    <img alt="npm beta version" src="https://img.shields.io/npm/v/semantic-release/beta.svg">
  </a>
</p>

**semantic-release** automates the whole package release workflow including: determining the next version number, generating the release notes, and publishing the package.

This removes the immediate connection between human emotions and version numbers, strictly following the [Semantic Versioning](http://semver.org) specification and communicating the **impact** of changes to consumers.

> Trust us, this will change your workflow for the better. – [egghead.io](https://egghead.io/lessons/javascript-how-to-write-a-javascript-library-automating-releases-with-semantic-release)

## Highlights

- Fully automated release
- Enforce [Semantic Versioning](https://semver.org) specification
- New features and fixes are immediately available to users
- Notify maintainers and users of new releases
- Use formalized commit message convention to document changes in the codebase
- Publish on different distribution channels (such as [npm dist-tags](https://docs.npmjs.com/cli/dist-tag)) based on git merges
- Integrate with your [continuous integration workflow](docs/recipes/release-workflow/README.md#ci-configurations)
- Avoid potential errors associated with manual releases
- Support any [package managers and languages](docs/recipes/release-workflow/README.md#package-managers-and-languages) via [plugins](docs/usage/plugins.md)
- Simple and reusable configuration via [shareable configurations](docs/usage/shareable-configurations.md)
- Support for [npm package provenance](https://github.com/Unity-Billal-mesloub/npm#npm-provenance) that promotes increased supply-chain security via signed attestations on GitHub Actions

## How does it work?

### Commit message format

**semantic-release** uses the commit messages to determine the consumer impact of changes in the codebase.
Following formalized conventions for commit messages, **semantic-release** automatically determines the next [semantic version](https://semver.org) number, generates a changelog and publishes the release.

Tools such as [commitlint](https://github.com/Unity-Billal-mesloub/commitlint) can be used to help contributors and enforce valid commit messages.

The table below shows which commit message gets you which release type when `semantic-release` runs (using the default configuration):

| Commit message                                                                                                                                                                                   | Release type                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------- |
| `fix(pencil): stop graphite breaking when too much pressure applied`                                                                                                                             | ~~Patch~~ Fix Release                                                                                           |
| `feat(pencil): add 'graphiteWidth' option`                                                                                                                                                       | ~~Minor~~ Feature Release                                                                                       |
| `perf(pencil): remove graphiteWidth option`<br><br>`BREAKING CHANGE: The graphiteWidth option has been removed.`<br>`The default graphite width of 10mm is always used for performance reasons.` | ~~Major~~ Breaking Release <br /> (Note that the `BREAKING CHANGE: ` token must be in the footer of the commit) |

### Automation with CI

**semantic-release** is meant to be executed on the CI environment after every successful build on the release branch.
This way no human is directly involved in the release process and the releases are guaranteed to be [unromantic and unsentimental](https://github.com/Unity-Billal-mesloub).

### Triggering a release

For each new commit added to one of the release branches (for example: `master`, `main`, `next`, `beta`), with `git push` or by merging a pull request or merging from another branch, a CI build is triggered and runs the `semantic-release` command to make a release if there are codebase changes since the last release that affect the package functionalities.

**semantic-release** offers various ways to control the timing, the content and the audience of published releases.
See example workflows in the following recipes:

- [Using distribution channels](docs/recipes/release-workflow/distribution-channels.md#publishing-on-distribution-channels)
- [Maintenance releases](docs/recipes/release-workflow/maintenance-releases.md#publishing-maintenance-releases)
- [Pre-releases](docs/recipes/release-workflow/pre-releases.md#publishing-pre-releases)

### Release steps

After running the tests, the command `semantic-release` will execute the following steps:

| Step              | Description                                                                                                                     |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Verify Conditions | Verify all the conditions to proceed with the release.                                                                          |
| Get last release  | Obtain the commit corresponding to the last release by analyzing [Git tags](https://git-scm.com/book/en/v2/Git-Basics-Tagging). |
| Analyze commits   | Determine the type of release based on the commits added since the last release.                                                |
| Verify release    | Verify the release conformity.                                                                                                  |
| Generate notes    | Generate release notes for the commits added since the last release.                                                            |
| Create Git tag    | Create a Git tag corresponding to the new release version.                                                                      |
| Prepare           | Prepare the release.                                                                                                            |
| Publish           | Publish the release.                                                                                                            |
| Notify            | Notify of new releases or errors.                                                                                               |

## Requirements

In order to use **semantic-release** you need:

- To host your code in a [Git repository](https://git-scm.com)
- Use a Continuous Integration service that allows you to [securely set up credentials](docs/usage/ci-configuration.md#authentication)
- A Git CLI version that meets [our version requirement](docs/support/git-version.md) installed in your Continuous Integration environment
- A [Node.js](https://nodejs.org) version that meets [our version requirement](docs/support/node-version.md) installed in your Continuous Integration environment

## Documentation

- Usage
  - [Getting started](docs/usage/getting-started.md)
  - [Installation](docs/usage/installation.md)
  - [CI Configuration](docs/usage/ci-configuration.md)
  - [Configuration](docs/usage/configuration.md#configuration)
  - [Plugins](docs/usage/plugins.md)
  - [Workflow configuration](docs/usage/workflow-configuration.md)
  - [Shareable configurations](docs/usage/shareable-configurations.md)
- Extending
  - [Plugins](docs/extending/plugins-list.md)
  - [Shareable configuration](docs/extending/shareable-configurations-list.md)
- Recipes
  - [CI configurations](docs/recipes/ci-configurations/README.md)
  - [Git hosted services](docs/recipes/git-hosted-services/README.md)
  - [Release workflow](docs/recipes/release-workflow/README.md)
- Developer guide
  - [JavaScript API](docs/developer-guide/js-api.md)
  - [Plugins development](docs/developer-guide/plugin.md)
  - [Shareable configuration development](docs/developer-guide/shareable-configuration.md)
- Support
  - [Resources](docs/support/resources.md)
  - [Frequently Asked Questions](docs/support/FAQ.md)
  - [Troubleshooting](docs/support/troubleshooting.md)
  - [Node version requirement](docs/support/node-version.md)
  - [Node Support Policy](docs/support/node-support-policy.md)

## Get help

- [GitHub Discussions](https://github.com/Unity-Billal-mesloub/semantic-release/discussions)
- [Stack Overflow](https://stackoverflow.com/questions/tagged/semantic-release)

## Badge

Let people know that your package is published using **semantic-release** and which [commit-convention](#commit-message-format) is followed by including this badge in your readme.

[![semantic-release: angular](https://img.shields.io/badge/semantic--release-angular-e10079?logo=semantic-release)](https://github.com/Unity-Billal-mesloub/semantic-release)

```md
[![semantic-release: angular](https://img.shields.io/badge/semantic--release-angular-e10079?logo=semantic-release)](https://github.com/Unity-Billal-mesloub/semantic-release)
```

## Team

| [![Billal-mesloub](https://avatars.githubusercontent.com/u/145295387?s=400&u=1c03bc195d2d338f2880f0d827e0b32b0fa685d6&v=4)](https://github.com/Unity-Billal-mesloub)|

## Alumni

| [![Billal-mesloub](https://avatars.githubusercontent.com/u/145295387?s=400&u=1c03bc195d2d338f2880f0d827e0b32b0fa685d6&v=4)](https://github.com/Unity-Billal-mesloub) | 

                                                 |

<p align="center">
  <img alt="Kill all humans" src="media/bender.png">
</p>
