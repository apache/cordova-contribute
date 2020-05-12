# Cordova and Node.js

Apache Cordova packages are written in JavaScript and run on Node.js. This is most obvious for the Cordova CLI, which you execute using the `cordova` command. But Cordova platforms, plugins and other packages also contain code that is executed by Node.js.

As such, we have some rules and guidelines about Cordova's Node.js usage:

## Compatibility and Testing

### Tooling (includes CLI) and Platforms

Cordova CLI, the tooling behind it and Cordova platforms all include scripts that are directly run by Node.js on the developer's machine. As such, we try to make sure those work on the indicate Node.js versions and test these scripts on a senseful collection of Node.js versions (latest supported, major versions, newest).

When a Node.js version is dropped from this support and testing roster, this manifests a major **breaking change** of said package.

### Plugins and Templates

Cordova Core Plugins and Templates on the other hand are not run locally but only contain JavaScript code that is executed in the context of the Cordova Webview on the end user's device (Exception: Plugin hooks, which no core plugin uses). This means that our CI testing does not have to run these on multiple Node.js versions, but can use only the newest and fastest Node.js version.

### Other

A special case is [`cordova-paramedic`](https://github.com/apache/cordova-paramedic), which is used by all core plugins to run plugin tests. While we control the Node.js version of that and thus could prefer newer Node.js versions, Paramedic can be used by _any_ plugin author to test their plugins as well - and as such has to be tested across multiple Node.js versions and should not drop support for older Node.js versions.

## Deprecation

TODO
Example blog post: https://cordova.apache.org/news/2019/04/11/nodejs-6.x-8.x-deprecation-timeline.html
