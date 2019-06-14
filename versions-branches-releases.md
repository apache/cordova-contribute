# Versions, Branches and Releases

This document describes how Apache Cordova versions and manages its packages.

- [Version](#version)
  * [Version Naming](#version-naming)
  * [Version Bump](#version-bump)
- [Branches](#branches)
  * [Release Branch](#release-branch)
- [Release](#release)
  * [Release Preparation](#release-preparation)
  * [Tags](#tags)
  * [Apache Process: Votes and Release Tags](#apache-process-votes-and-release-tags)
  * [Publish](#publish)
- [Release Process Documentation](#release-process-documentation)

## Version

### Version Naming

- Versions of packages follow simple [Semantic Versioning](https://semver.org/) practices:
  > Given a version number MAJOR.MINOR.PATCH, increment the:
  > - MAJOR version when you make incompatible API changes,
  > - MINOR version when you add functionality in a backwards-compatible manner, and
  > - PATCH version when you make backwards-compatible bug fixes.
- A `-dev` suffix is added to versions in repos to indicate unreleased code (as platforms and plugins can be installed from a repository's `master` branch via Cordova CLI). This suffix is only removed during the [release process](#release) and added back with the [version bump](#version-bump).

### Version Bump

The version of a package is "bumped" (increased):

- automatically (after release)
  - in preparation of next release: bump patch  (`#.#.x`)
- manually (when it happens or latest before release)
  - on commits adding new features: bump minor (`#.x.#`)
  - on commit breaking existing functionality: bump major (`x.#.#`)

If a [release branches](#release-branch) is required, the version bump may happen on the release branch instead of `master`.

## Branches

Apache Cordova uses a variant of [Trunk Based Development](https://trunkbaseddevelopment.com):

- Feature development is done in feature branches or branches of forks. 
- Those are merged via Pull Requests that integrate their changes back into `master`.
- [Release branches](#release-branch) are used for releases if necessary.

### Release Branch

Cordova uses release branches for releases only if necessary: If a new patch or minor release from `master` is not possible as it already includes other changes that should or can not be part of the planned release, we create a release branch (e.g. `1.0.x` for an upcoming `1.0.1` patch release, or `2.1.x` for an upcoming `2.1.0` minor release). New changes added in those release branches should be merged back to `master` if applicable (release notes or bug fixes: yes, version number changes: no).

## Release

### Release Preparation

During the release preparation the commit messages of changes that happened are curated into a release notes file.

### Tags

Tags are used to to indicate versions (e.g. `1.1.0`). Tagging happens after all the work for a release has been done.

### Apache Process: Votes and Release Tags

As Cordova is an Apache Software Foundation project, we have some additional special steps during our releases:

- When tagging a "release" you do not use the final release version number, but e.g. `vote/1.1.0` to indicate that this is not a release tag that still has to be voted on.
- This tag is then archived into an archive and uploaded to a temporary location on the Apache SVN server.
- Then there is a [release vote on the mailing list](release-voting.md) to determing if the release can happen as planned.
- Voted on and accepted releases get an additional permanent "release tag" (e.g. `1.1.0`) and the archive is moved to another, permanent location on the Apache SVN server.

### Publish

After a successful vote the tag is also be published to [npm](https://www.npmjs.com/) for developers to use with Cordova CLI.

## Release Process Documentation

The actual release process a committer might follow is documented in [release-process.md](release-process.md). This also describes the software Apache Cordova uses to enable and simplify the release process.
