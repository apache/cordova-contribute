# Release Process Documentation

- Supported by automation via `cordova-coho` CLI tool

## Release Process Overview

- Decide on release type:   
  a) major/minor  
  b) patch
- Switch to correct branch:   
  - If minor/major: `master`  
  - If patch: existing release branch
- Prepare Release (Make sure branch is good to release)
  - If patch: Cherry pick fixes from `master` or add on release branch
  - [Code Maintenance](TODO)
  - [Test](TODO)
  - If major (and not bumped manually before): Bump major
  - Create, curate and commit Release Notes
- Release
  - If minor/major: Create new release branch
  - Remove `-dev` suffix
  - Tag on release branch
  - Apache: Create archive and upload to `dist/dev`
  - Bump patch + add `-dev` back on release branch
  - If major/minor: Bump minor (and make sure `-dev` is present) on `master`
- Vote
- On success:
  - Apache: Promote from `dist/dev` to `dist`
  - Apache: Add `rel/` tag
  - Publish to npm
  - If patch: Cherry pick release notes commit from release branch to `master`
  
## Detailed Release Process Documentation

- Tooling
- Platforms
- Plugins
- Other
