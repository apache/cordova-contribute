# Release Process Documentation

## Release Process Overview

This describes the _technical_, theoretical steps of a release. (For all the _organizational_ steps and actual commands to execute, please refer to the [Detailed Release Process Documentation](#detailed-release-process-documentation) below.)

- Decide on release type:   
  a) major/minor  
  b) patch
- Checkout correct branch:   
  - If minor/major: `master`  
  - If patch: existing release branch
- Prepare Release (Make sure branch is good to release)
  - If patch: _Cherry pick_ fixes from `master` (or create on release branch directly or via PR and _commit_)
  - [Code Maintenance](code-maintenance.md)
  - [Test](testing-releases.md)
    - Fix any regressions and _commit_
  - If major (and not bumped manually with breaking commit before): Bump major and _commit_
  - Create, curate Release Notes into `RELEASENOTES.md` and _commit_
- Release
  - If minor/major: _Create_ new release branch
  - Remove `-dev` suffix (and _commit_)
  - [Test](testing-releases.md)
  - _Tag_ on release branch
  - Apache: Create archive and upload to `dist/dev`
  - Bump patch + add `-dev` back on release branch (and _commit_)
  - If minor/major: Bump minor (and make sure `-dev` is present) on `master` (and _commit_)
  - _Push_ all changes, release branch and tag
- Vote
  - Other PMC members [test the release](testing-releases.md) and vote
- On success:
  - Apache: Promote from `dist/dev` to `dist`
  - Apache: Add `rel/` tag
  - Publish to npm
  - If patch: Cherry pick release notes (and additional) commit from release branch to `master`
  - _Push_ changes and tag
- On failure:
  - Remove created tag, delete uploaded archive from `dist/dev`, unbump patch on release branch (and _commit_ and _push_)
  - Fix problem
  - Restart at "Release"

This list also does not include steps that are only required for one type of component.

TODO
- Platforms: Update `cordova.js` and propagate version number to other platform files

But they are included below.

## Detailed Release Process Documentation

This generalized release process is supported and partly automated by our `cordova-coho` CLI tool. As details of this process are different depending on what kind of package you want to release, we have individual detailed release process documentation that contains the actual commands to run:

- [Platforms](https://github.com/apache/cordova-coho/blob/master/docs/platforms-release-process.md)
- [Plugins](https://github.com/apache/cordova-coho/blob/master/docs/plugins-release-process.md)
- [Tooling](https://github.com/apache/cordova-coho/blob/master/docs/tools-release-process.md)
- [Hello World App](https://github.com/apache/cordova-coho/blob/master/docs/app-hello-world-release-process.md)
- [Coho](https://github.com/apache/cordova-coho/blob/master/docs/coho-release-process.md)
