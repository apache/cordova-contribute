# Cordova and Node.js

Cordova CLI locally runs on Node.js  
CLI uses specific node versions

https://cordova.apache.org/news/2019/04/11/nodejs-6.x-8.x-deprecation-timeline.html

## Tooling and Platforms

Include scripts that are run on node, so node versions have to be tested  
Dropping a node version is a major breaking change

## Plugins and Templates

Usually only run on the devices, not locally  
Exception: Hooks  
CLI does not have to test on all node versions  
Enough to use one Node version, newest and fastest  
Plugin test tooling (paramedic) still has to work for all node versions though :/
