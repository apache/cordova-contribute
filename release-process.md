# Release Process Documentation

## Release Process Overview

This describes the _technical_, theoretical steps of a release. (For all the _organizational_ steps and actual commands to execute, please refer to the [Detailed Release Process Documentation](#detailed-release-process-documentation) below.)

- Checkout `master` of the project you want to release
- Find out if your release requires a release branch (instead of releasing from `master` directly):  
  a) Are there any commits on `master` that should not be part of the release?  
  b) If patch release: Is there already a release branch for a previous patch release for this minor version?  
  c) Do you want to do a patch release to an older minor (`1.2.3` after `1.3.0` has already been released) or a minor release after there was a new major release (`1.7.0` after `2.0.0` has already been released)
- Only if yes: 
  - _Create_ a release branch (e.g. `1.2.x`) on the last "good" commit (before the first one that should not be included in the release) or last released tag/commit and _check it out_ (or _check out_ the existing release branch for b))
  - _Cherry pick_ any further commits from `master` that should be included to the checked out release branch
  - Do any manual changes that need to be done (e.g. to fix a bug) and _commit_ 
- Prepare Release
  - [Code Maintenance](code-maintenance.md)
  - If minor or major release (and not bumped manually already): Bump minor or major and _commit_
  - [Test](testing-releases.md)
    - Fix any regressions and _commit_
  - Create, curate Release Notes into `RELEASENOTES.md` and _commit_
- Release
  - Remove `-dev` suffix in version and Release Notes (and _commit_)
  - _Tag_ as `vote/x.y.z`
  - Apache: Create archive and upload to [`dist/dev`](https://dist.apache.org/repos/dist/dev/cordova/)
  - Bump patch + add `-dev` back (and _commit_)
  - _Push_ all changes and tag
- Vote
  - Other PMC members [test the release](testing-releases.md) and vote
- On success:
  - Apache: Promote from [`dist/dev`](https://dist.apache.org/repos/dist/dev/cordova/) to [`dist/release`](https://dist.apache.org/repos/dist/release/cordova/)
  - Add `x.y.z` release tag
  - Publish archive (!) to npm
  - If releasing from release branch: Cherry pick release notes (and possible other commits) to `master`
  - _Push_ changes and tag
- On failure:
  - Remove created tag (and _push_), delete uploaded archive from [`dist/dev`](https://dist.apache.org/repos/dist/dev/cordova/), unbump patch on release branch (and _commit_ and _push_)
    - TODO ALTERNATIVE: remove tag, delete archive, start from beginning with now a patch release
    - TODO ALTERNATIVE: https://github.com/apache/cordova-coho/blob/master/docs/platforms-release-process.md#if-the-vote-does-not-pass
  - Fix problem
  - Restart at "Release"

This list also does not include steps that are only required for one type of component:

- Platforms: Update `cordova.js`, propagate version number to other platform files (which those are depends on the platform), tag `master` of `cordova-js` with new platform version, make sure documentation is up to date or create PR that can be merged after release, Android only: Publish to Bintray
- Plugins: Make sure `README.md` is correct
- Tools: cordova-lib: Update `platformsConfig.json`, all: update cross dependencies between libraries, 

The detailed documentation below does include these at the appropriate locations.

## Detailed Release Process Documentation

This generalized release process is supported and partly automated by our `cordova-coho` CLI tool. As details of this process are different depending on what kind of package you want to release, we have individual detailed release process documentation that contains the actual commands to run:

- [Platforms](https://github.com/apache/cordova-coho/blob/master/docs/platforms-release-process.md)
- [Plugins](https://github.com/apache/cordova-coho/blob/master/docs/plugins-release-process.md)
- [Tooling](https://github.com/apache/cordova-coho/blob/master/docs/tools-release-process.md)
- [Hello World App](https://github.com/apache/cordova-coho/blob/master/docs/app-hello-world-release-process.md)
- [Coho](https://github.com/apache/cordova-coho/blob/master/docs/coho-release-process.md)
