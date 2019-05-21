# Versioning and Releases

This document describes how Apache Cordova versions and manages its packages.

- [Version](#version)
  * [Version Naming](#version-naming)
  * [Version Bump](#version-bump)
- [Branches](#branches)
- [Release](#release)
  * [Release Preparation](#release-preparation)
  * [Tags](#tags)
  * [Release Branch](#release-branch)
  * [Apache way: Votes and Release Tags](#apache-way-votes-and-release-tags)
  * [Publish](#publish)
- [Release Process Documentation](#release-process-documentation)

## Version

### Version Naming

- Versions of packages follow simple [Semantic Versioning](https://semver.org/) practices:
  > Given a version number MAJOR.MINOR.PATCH, increment the:
  > - MAJOR version when you make incompatible API changes,
  > - MINOR version when you add functionality in a backwards-compatible manner, and
  > - PATCH version when you make backwards-compatible bug fixes.
- A `-dev` suffix is added to versions in repos to indicate unreleased code (as platforms and plugins can be installed from `master` via CLI). It is temporarily removed during the [release process](#release) and added back with the [version bump](#version-bump) that h

### Version Bump

The version of a package is "bumped" (increased):

- automatically 
  - after release, in preparation of next release: 
    - on minor or major release: bump minor (on `master`)
    - on patch release: bump patch (on release branch)
- manually
  - on breaking commit (or latest before release): bump major

## Branches

Apache Cordova uses a variant of [Trunk Based Development](https://trunkbaseddevelopment.com):

- Feature development is done in feature branches or branches of forks. 
- Those are merged via Pull Requests that integrate their changes back into `master`.
- [Release branches](#release-branch) are used for patch releases.

## Release

### Release Preparation

During the release preparation the commit messages of changes that happened are curated into a release notes file.

### Tags

Tags are used to to indicate versions (e.g. `1.1.0`). Tagging happens after all the work for a release has been done.

### Release Branch

Cordova uses release branches for (possible) future patch releases: On the release of a new minor or major version of a package a new release branch (e.g. `1.0.x` for a `1.0.0` release) is automatically created. Future bug fixes should usually be cherry picked from `master` to that release branch before releasing a patch update.

### Apache way: Votes and Release Tags

- Tags are archived into a file and uploaded to a temporary location on the Apache SVN server
- Then there is a [release vote on the mailing list](release-voting.md)
- Voted on and accepted releases get an additional permanent "release tag" (e.g. `rel/1.1.0`) and are moved to another, permanent location on the Apache SVN server

### Publish

After a successful vote the tag is also be published to [npm](https://www.npmjs.com/) for developers to use with Cordova CLI.

## Release Process Documentation

The actual release process a committer might follow is documented in [release-process.md](release-process.md). This also describes the software Apache Cordova uses to enable and simplify the release process.
