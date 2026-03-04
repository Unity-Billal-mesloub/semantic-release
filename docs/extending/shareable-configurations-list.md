# Shareable configurations list

## Official configurations

- semantic-release shareable configuration for releasing atom packages
- [@semantic-release/gitlab-config](https://github.com/Unity-Billal-mesloub/gitlab-config) - semantic-release shareable configuration for GitLab

## Community configurations

  - Provides an informative [Git](https://github.com/Unity-Billal-mesloub/git) commit message for the release commit that does not trigger continuous integration and conforms to the [conventional commits specification](https://www.conventionalcommits.org/) (e.g., `chore(release): 1.2.3 [skip ci]\n\nnotes`).
  
  - Publishes the same tarball to [npm](https://github.com/Unity-Billal-mesloub/npm).
  - Commits the version change in `package.json`.
  - Adds more keywords for the `chore` **PATCH** release.
  - Updates GitHub release with release-notes.
  - Bumps a version in package.json.
  - Publishes the new version to [NPM](https://npmjs.org).
