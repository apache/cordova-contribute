# Testing Releases


## Get the Code

a) Before the release was actually made:

...

b) After the release was made and you now want to make sure the archive is good:

...

## Test the Release

- `npm test`

### Plugins

#### Plugin Tests

Create a new app, add the plugin and its tests subplugin:

```bash
cordova create pluginTestApp
cd pluginTestApp
cordova plugin add ../cordova-plugin-vibration
cordova plugin add ../cordova-plugin-vibration/tests
cordova plugin add cordova-plugin-test-framework
sed -i -e 's/index.html/cdvtests\/index.html/g' config.xml
cordova platform add android
cordova run android
```

This should start a grey-ish app with "Auto Tests" and "Manual Tests" buttons. You should run both and see if all/most/the expected ones succeed.

#### Plugin Tests via Mobilespec

Assumes plugin is checkout out next to `cordova-mobile-spec`:

```bash
node cordova-mobile-spec/createmobilespec/createmobilespec.js --android --global --plugins="cordova-plugin-vibration"
```

This should start a black-ish app with a "Plugin tests" button. When clicking it you end up in a screen with "Auto Tests" and "Manual Tests" buttons. You should run both and see if all/most/the expected ones succeed.

### Platforms

TODO

The following commands all assume to be run in a folder that includes the platform you are testing, e.g. `cordova-android`. It should also contain a checkout of `cordova-mobile-spec`.

#### Platform + Plugins

Create and run a [mobile-spec](https://github.com/apache/cordova-mobile-spec/) project:

```bash
./cordova-mobile-spec/createmobilespec/createmobilespec.js --android --forceplugins
(cd mobilespec && cordova run android --device)
(cd mobilespec && cordova run android --emulator)
```

This should start a black-ish app with a "Plugin tests" button. When clicking it you end up in a screen with "Auto Tests" and "Manual Tests" buttons. You should run both and see if all/most/the expected ones succeed.

#### Hello World app via CLI

Create a hello world app using `cordova`:

```bash
cordova create ./androidTest org.apache.cordova.test androidTest
(cd androidTest && cordova platform add ../cordova-android)
(cd androidTest && cordova run android --device)
(cd androidTest && cordova run android --emulator)
```

This should create an app showing the Cordova logo, "Apache Cordova" and a green "Device is ready" box.

#### `/bin` scripts

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

### Tooling

TODO

### Other

TODO
