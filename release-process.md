# Release Process Documentation

- Supported by automation via `cordova-coho` CLI tool


## Release Process Overview

- Decide on release type: major, minor, patch
- Switch to correct branch:   
  a) minor/major: `master`  
  b) patch: release branch
- If major (and not bumped manually before): Bump major
- Make sure branch is good to release
  - Code Maintenance
  - Test
- Release
  - Create and curate Release Notes
  - If minor/major: Create new release branch
  - Remove `-dev` suffix
  - Tag on release branch
    - Publish to dist/dev
  - Bump minor + add `-dev` back
  - If patch: Cherry pick useful changes back to `master`
- Vote
- On success:
  - Promote from dist/dev to dist
  - Add rel/ tag
  
## Detailed Release Process Documentation

- Tooling
- Platforms
- Plugins
- Other
