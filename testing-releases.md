# Testing Releases

This document describes how to test a release of a Apache Cordova component before and while the "[Creating a Release](release-process.md)" process.

- [General](#general)
  * [Get the Code](#get-the-code)
  * [General Testing](#general-testing)
- [Plugins](#plugins)
  * [Plugin Tests](#plugin-tests)
  * [Plugin Tests via Mobilespec](#plugin-tests-via-mobilespec)
- [Platforms](#platforms)
  * [Platform + Plugins via Mobilespec](#platform--plugins-via-mobilespec)
  * [Hello World app via CLI](#hello-world-app-via-cli)
  * [`/bin` scripts](#bin-scripts)
  * [`cordova-lib` tests](#cordova-lib-tests)
  * [cordova.js](#cordovajs)
- [Tooling](#tooling)
- [Other](#other)

## General

### Get the Code

The code of the component you want to test should be in a folder with the name of the component (e.g. `cordova-plugin-vibration` or `cordova-ios`):

a) Before the release was actually made: The component should be checked out via git.  
b) After the release was made and you now want to make sure the archive is good to be able to [vote for it](verify-release-vote.md): Download the `.tgz` source code artifact linked in the `[VOTE]` email on the dev mailing list. Unpack the archive, and move the content of `package` into a folder named after the component, then run `npm install` to install the dependencies.

### General Testing

- `npm test`: All packages define a `test` command that should pass locally.

## Plugins

### Plugin Tests

Create a new app, add the plugin, its tests subplugin, and `cordova-plugin-test-framework` that allows running those tests:

```bash
cd ..
cordova create pluginTestApp
cd pluginTestApp
cordova plugin add ../cordova-plugin-vibration
cordova plugin add ../cordova-plugin-vibration/tests
cordova plugin add cordova-plugin-test-framework
sed -i -e 's/index.html/cdvtests\/index.html/g' config.xml # change `config.xml` to contain `<content src="cdvtests/index.html" />`
cordova platform add android
cordova run android
```

This should start a grey-ish app with "Auto Tests" and "Manual Tests" buttons. You should run both and see if they succeed.

### Plugin Tests via Mobilespec

Historically the release process documentation also advised developers to use `cordova-mobile-spec` to create an app that includes the [Plugin Tests](#plugin-tests). As this is error prone and doesn't give additional insight to the [Plugin Tests](#plugin-tests), it is not recommended any more.

<details>
  <summary>Instructions</summary>

```bash
node cordova-mobile-spec/createmobilespec/createmobilespec.js --android --global --plugins="cordova-plugin-vibration"
```

This should start a black-ish app with a "Plugin tests" button. When clicking it you end up in a screen with "Auto Tests" and "Manual Tests" buttons. You should run both and see if all/most/the expected ones succeed.
</details>

## Platforms

TODO

The following commands all assume to be run in a folder that includes the platform you are testing, e.g. `cordova-android`. It should also contain a checkout of `cordova-mobile-spec`.

### Platform + Plugins via Mobilespec

Create and run a [mobile-spec](https://github.com/apache/cordova-mobile-spec/) project:

```bash
./cordova-mobile-spec/createmobilespec/createmobilespec.js --android --forceplugins
(cd mobilespec && cordova run android --device)
(cd mobilespec && cordova run android --emulator)
```

This should start a black-ish app with a "Plugin tests" button. When clicking it you end up in a screen with "Auto Tests" and "Manual Tests" buttons. You should run both and see if all/most/the expected ones succeed.

### Hello World app via CLI

Create a hello world app using `cordova`:

```bash
cordova create ./androidTest org.apache.cordova.test androidTest
(cd androidTest && cordova platform add ../cordova-android)
(cd androidTest && cordova run android --device)
(cd androidTest && cordova run android --emulator)
```

This should create an app showing the Cordova logo, "Apache Cordova" and a green "Device is ready" box.

### `/bin` scripts

Run your platform's `./bin/create` script and run the resulting project:

```bash
./cordova-android/bin/create ./androidTest2 org.apache.cordova.test2 androidTest2
(cd androidTest2 && ./cordova/build)
(cd androidTest2 && ./cordova/run --device)
(cd androidTest2 && ./cordova/run --emulator)
```

This should create an app showing a white screen.

Ensure the generated project files also build through the appropriate platform IDE.

The output from `./cordova/version` should show the correct platform version.

### `cordova-lib` tests

TODO https://github.com/apache/cordova-coho/blob/master/docs/platforms-release-process.md#4-cordova-lib-tests

### cordova.js

TODO Some kind of tests (maybe via plugins) that test if the cordova.js functionality works as expected

## Tooling

TODO https://github.com/apache/cordova-coho/blob/master/docs/tools-release-process.md#test

## Other

TODO https://github.com/apache/cordova-coho/blob/master/docs/tools-release-process.md#test
TODO https://github.com/apache/cordova-coho/blob/master/docs/coho-release-process.md#test
