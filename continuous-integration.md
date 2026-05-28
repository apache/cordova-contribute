# Continuous Integration

Apache Cordova uses Continuous Integration to run [tests](testing.md) and other checks for all our software. TODO

## Tooling

TODO

## Platforms

TODO

## Plugins

### How to create the CI configuration for plugins

- Travis CI
  - Take the `travis.yml` from [cordova-paramedic](https://github.com/apache/cordova-paramedic) and copy it to the plugin repository
  - Adapt the repository specific `addons.jwt.secure` key to what was in `travis.yml` before
  - Done.
- AppVeyor
  - TODO
