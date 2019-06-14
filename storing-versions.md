# Storing Versions

Usually npm based packages, as Apache Cordova uses to distribute its components, store the version in a `version` field of the `package.json` file. For various reasons, some of Cordova's packages also store the version string in other locations:

## Details

### Platforms

- `VERSION` file in the root of the repository or native library. When a platform is installed, `package.json` is not copied over, so `VERSION` is used to find out what version of a platform is actually installed
- `bin/templates/scripts/cordova/version` (or equivalent script per platform) has another copy
- Platform specific:
  - Android
    - `build.gradle` has `version` or similar
    - `.java` file that has a `CORDOVA_VERSION`
  - iOS
    - `CDVAvailability.h` has two `#define` lines that list the version

### Plugins

- `plugin.xml`, `version` attribute of `plugin` tag
- Plugins contains a `tests` "plugin" that has its own `package.json` and `plugin.xml` that has a synchronized version string as the main plugin

## Automation

- Updating of these version strings should be automated and not a manual task
- `updateRepoVersion` method of `cordova-coho` contains a list of locations that are updated by tooling
  - https://github.com/apache/cordova-coho/blob/master/src/versionutil.js#L90
  - Also other method
    - https://github.com/apache/cordova-coho/blob/master/src/platform-release.js#L107

