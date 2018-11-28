# Testing Cordova Plugins

## Writing tests

### Unit Tests


jasmine

### Integration Tests

1. `/tests` in app
2. https://github.com/apache/cordova-plugin-test-framework
3. `cdvtests/index.html`


Install plugin and its tests in an app:

```
cordova plugin add https://github.com/apache/cordova-plugin-file-transfer.git
cordova plugin add plugins/cordova-plugin-file-transfer/tests # local tests that were downloaded with previous commands
cordova plugin add https://github.com/apache/cordova-plugin-test-framework
```








## Manual



## Automated

eslint
paramedic
  appium tests

### CI

Continuous Integration of Cordova plugins uses multiple providers:

- Travis for Linux
- AppVeyor for Windows

There is no (or: only sometimes) direct testing on macOS (on Travis).

#### Sauce Labs

But integration tests are run on Saucelabs on many different devices, emulators and browsers (Android, iOS, Firefox, Safari, Chrome etc.). 

The tests are executed via Travis, which triggers `cordova-paramedic`.  
The tests are written in Appium.  
The list of platforms to test is configured in `.travis.yml`.  
The paramedic command is triggered after running all other tests.

##### Credentials

Account `snay`

```yaml
addons:
  jwt:
    secure: QivPLlqTVvOo3TJeHxuBOfxU6lho1I0IxQ3b68yntkEQQJko6kzleXHfgjf0a8aw8m38E3+fxaBWF1bGyucGwOLDWY8Ddt2P2xg44zdXH5EXHd9oIqAgngIdzLvUtH3Db2TbQEtIGOkrnNR2STovjqB7vHGLASQrgs4oL7r32/s=
```

encrypted SAUCE_ACCESS_KEY with https://docs.travis-ci.com/user/jwt
