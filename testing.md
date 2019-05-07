# Testing Cordova

The aim of Cordova's developer team is to produce great and working software. To achieve this, we invested a lot of time into making Cordova testable. This document should give a general overview about our testing practices and setup.

## Table of Contents

- [What is the current state of the tests?](#what-is-the-current-state-of-the-tests)
- [What types of tests does Cordova use?](#what-types-of-tests-does-cordova-use)
  * [Manual Tests](#manual-tests)
  * [Automated Tests](#automated-tests)
    + [Syntax Checker](#syntax-checker)
    + [Unit Tests](#unit-tests)
      - [Code Coverage](#code-coverage)
    + [Component Tests](#component-tests)
    + [Integration / End to End Tests](#integration--end-to-end-tests)
      - [Appium Interface Tests](#appium-interface-tests)
- [How to implement tests?](#how-to-implement-tests)
  * [Tooling](#tooling)
  * [Platforms](#platforms)
    + [Native Unit Tests](#native-unit-tests)
  * [Plugins](#plugins)
    + [Native](#native)
    + [Plugin tests with `cordova-plugin-test-framework`](#plugin-tests-with-cordova-plugin-test-framework)
    + [Appium Tests](#appium-tests)
    + [Paramedic: `cordova-paramedic`](#paramedic-cordova-paramedic)
      - [Sauce Labs](#sauce-labs)
    + [Core Plugins](#core-plugins)
    + [3rd party plugins](#3rd-party-plugins)
- [How to run tests?](#how-to-run-tests-)
  * [Local](#local)
    + [Special case: Plugins](#special-case-plugins)
  * [Continuous Integration](#continuous-integration)

<!--<small><i><a href='http://ecotrust-canada.github.io/markdown-toc/'>Table of contents generated with markdown-toc</a></i></small>-->

## What is the current state of the tests?

If you are only interested in the [current build status](#continuous-integration) of the repositories and [how much of the code is covered by tests](#code-coverage) you can check our [Cordova Status Dashboard](https://apache.github.io/cordova-status/). It shows badges for each CI provider that indicate the current build status and a badge that contains the % of code coverage for each repository. Click each badge for more information.

If you are interested in how all this works, please read on:

## What types of tests does Cordova use?

Cordova projects use several different types of tests:

### Manual Tests

- Check if some manual action produces the expected result.
- Manual tests are often not explicitly documented, but implicitly assumed. If there is an actual implementation, it is much more "free form" as with the other test types mentioned on this page: E.g. for [plugins](#plugins), manual tests are defined as a list of buttons to tap and an "Expected result" text below the button.

### Automated Tests

#### Syntax Checker

- Check if the code of a project follows specific syntax guidelines.  
- Usually uses [`eslint`](https://eslint.org/), which is "a fully pluggable tool for identifying and reporting on patterns in JavaScript".

#### Unit Tests

- Check if individual pieces of code produce the expected results.
- All Cordova projects use [`jasmine`](https://jasmine.github.io/) to write and run **unit tests** for their JavaScript code: "Jasmine is a behavior-driven development framework for testing JavaScript code."
- For their native code some projects use the appropriate tools of the platform to run tests: e.g. `gradle` for running Android JUnit tests, `xcodebuild test` for running [iOS XCTests](https://developer.apple.com/documentation/xctest)

##### Code Coverage

- Check how much of the code base is covered by the previously run Unit Tests.
- Some Cordova projects (see the Codecov badges [here](https://github.com/apache/cordova-status)) collect code coverage by using [`nyc`](https://github.com/istanbuljs/nyc) (e.g. `cordova-android`, `cordova-android`) and report the results to [Codecov](https://codecov.io/) for tracking and visualization.

#### Component Tests

- Check if an individual piece of code, interacting with an external component, produces the expected results.
- Component tests are used in a few places, and are also written with `jasmine`.

#### Integration / End to End Tests

- Check if multiple pieces of code or software work together as expected.
- `jasmine` is also used to write and execute end to end tests.

##### Appium Interface Tests

- Check the app behavior by simulating actual user input.
- Appium tests also use `jasmine` syntax for the general testing setup, but the [Webdriver API](https://www.w3.org/TR/webdriver1/) to simulate and drive interactions with the app on the device.
<!-- TODO Means that the native code is being exercised. -->

## How to implement tests?

### Tooling

TODO

### Platforms

TODO `/spec`

#### Native Unit Tests

Additionally to the usual unit tests explained above, for the platforms there can also be **native unit tests**. Those usually live in `/test(s)` and come in the form of a native test project that interacts with the main platform code. They can also be run via a `npm run ...` command that triggers a Javascript file in the test directory.

For Android for example:
- https://github.com/apache/cordova-android/blob/master/test/
- https://github.com/apache/cordova-android/blob/master/test/run_java_unit_tests.js
- `npm run java-unit-tests`

### Plugins

Plugin tests are somewhat special, as they are set up in a different way. `npm run tests` just includes the syntax check, while the real tests are run by other means:

#### Native

TODO

Examples:
- https://github.com/apache/cordova-plugin-camera/tree/master/tests/ios
- https://github.com/apache/cordova-plugin-splashscreen/tree/master/tests/ios
- https://github.com/apache/cordova-plugin-wkwebview-engine/tree/master/tests/ios

#### Plugin tests with `cordova-plugin-test-framework`

The actual tests can be found as `test.js` in a `/tests` folder. The automated tests, exported as `defineAutoTests`, use the familiar `jasmine` syntax, while the manual tests can be any HTML elements - usually buttons that trigger a JS function, with a description of the expected result underneath - exported via `defineManualTests`.

Additionally, the `/tests` folder contains its own `package.json` and `config.xml` to create a "mini test plugin" to be used by [`cordova-plugin-test-framework`](https://github.com/apache/cordova-plugin-test-framework) to create a test interface (manual UI and `jasmine` test runner) that is viewable inside an app: Create a new app, add the plugin, add the "tests" sub-plugin and you can navigate to `cdvtests/index.html` in your app to view that test interface.

#### Appium Tests

A small number of plugins also implements End to End Tests with Appium. They live in `/appium-tests`.
TODO Native code is being execised vs. JS part with all the other test types

#### Paramedic: `cordova-paramedic`

To automate the creating of a test app and the test execution process [`cordova-paramedic`](https://github.com/apache/cordova-paramedic) can be be used:

1. Install `cordova-paramedic` (`npm install -g ...` or clone + `npm install`)
2. Run Paramedic for the current plugin:  
    ```
    node /tmp/paramedic/main.js 
      --config pr/$PLATFORM 
      --plugin $(pwd) 
    ```
3. App is built, setup; Tests are run and results reported

##### Sauce Labs

Paramedic can also run these tests on a remote service called Sauce Labs. They offer emulators and real devices of all kind to run testing on. Both normal plugin tests and Appium tests are executed on Sauce Labs on different operating systems and operating system versions.

#### Core Plugins

(Almost) All Core Plugins implement tests in the previously described ways. Some focus on automated tests, some on manual ones. The plugin tests are executed on CI by the already mentioned `cordova-paramedic` on Sauce Labs.

#### 3rd party plugins

TODO

Some have tests, not very many unfortunately.


## How to run tests?

### Local

As all Cordova projects are set up as JavaScript projects, the available test commands are usually defined in the `scripts` array of `package.json`. An example from `cordova-android`:

```json
  "scripts": {
    "test": "run-s eslint unit-tests java-unit-tests e2e-tests",
    "eslint": "run-s -c eslint:*",
    "eslint:scripts": "eslint bin spec test",
    "eslint:bins": "eslint 'bin/**/*' --ignore-pattern '**/*.*' --ignore-pattern '**/gitignore' --ignore-pattern 'bin/templates/cordova/version'",
    "unit-tests": "jasmine --config=spec/unit/jasmine.json",
    "java-unit-tests": "node test/run_java_unit_tests.js",
    "e2e-tests": "jasmine --config=spec/e2e/jasmine.json",
    "cover": "istanbul cover --root bin --print detail jasmine -- --config=spec/unit/jasmine.json"
  },
```

This defines different keywords that can be used for `npm run ...`, i.e. `npm run test`. In this case `test` is a combination of sub-commands, that can also be run individually.

Contributors are expected to use those commands before, during and after making changes to the codebase to ensure that the tests still pass.

#### Special case: Plugins

As plugin tests are implemented in a special way, read [how to implement and run plugin tests below](#plugins).

### Continuous Integration

The same npm scripts are also used in CI environments to run tests. Each CI service in use usually has a configuration file in the repository under test, e.g. `.travis.yml` for Travis CI. These configuration files define the setup and commands to run on each build, which usually includes `npm run test` or similar commands to run these tests.

<!--

## Missing bits

- Proper integration tests of CLI and platforms
- Testing installation of 3rd party plugins
- Testing installation of core plugins


#### Command line
#### Emulators or Devices
#### Remote Emulators or Devices

-->
