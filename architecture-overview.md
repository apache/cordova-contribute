# Architecture overview

To get an architecture overview of Apache Cordova and how it works and how all its [many libraries](https://github.com/apache/cordova) are connected, it makes sense to follow the journey a typical user of Cordova would take:

## `$ npm install -g cordova`

The installation instructions tell the user run `npm install -g cordova`. This installs the [`cordova` npm package](https://www.npmjs.com/package/cordova), which is the published version of the code in the [apache/cordova-cli](https://github.com/apache/cordova-cli) repository.

### cordova-cli

The user then can run commands like `cordova -v` in their command line, which executes the `bin/cordova` program (or `bin/cordova.cmd` on Windows, which just executes `bin/cordova` with node) that is installed in the global npm packages directory.

When installing `cordova-cli`, the user also installed two other Cordova libraries via the [dependencies in `package.json`](https://github.com/apache/cordova-cli/blob/master/package.json) (next to several other, external libraries) : `cordova-common` and `cordova-lib`.

`cordova-cli` itself is a pretty thin layer of code that handles parsing and redirecting the commands the CLI can execute over to `cordova-lib`. Besides, it handles outputting the `help` commands and prompting for permission and sending telemetry data. From `cordova-common` is uses mainly the logger and some error handling.

### cordova-common

[cordova-common](https://github.com/apache/cordova-common) contains what it says with its name: Common functionality that is used by other Cordova libraries like `cordova-cli` or `cordova-lib` and others. It has [no further Cordova library dependencies](https://github.com/apache/cordova-common/blob/master/package.json).

### cordova-lib

[cordova-lib](https://github.com/apache/cordova-common) on the other hand is the heart of the Cordova CLI: Most commands executed with `cordova-cli` are then actually handled by `cordova-lib`. For that [it has dependencies](https://github.com/apache/cordova-lib/blob/master/package.json) on the rest of the Cordova tooling libraries: `cordova-common` (again), `cordova-create`, `cordova-fetch`, `cordova-serve` and `cordova-js`. <!-- TODO Remove `cordova-js` when possible -->

To understand how those are used, it is best to look at some Cordova CLI command the user will execute:

## `$ cordova create`

If they don't have a project via Git or download, they will run `cordova create` to create a new Cordova project. 

TODO

### cordova-create

## `$ cordova info`

## `$ cordova platform add ...`

### cordova-fetch

Adds platform
  pinned versions

contains default plugins

## `$ cordova plugin add ...`

manually add plugins

## `$ cordova serve`

### cordova-serve

## `$ cordova prepare/compile/clean/run(/emulate/build) ...`

CLI command to run/emulate/build platform

## `$ cordova requirements`
