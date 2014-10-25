# grunt-node-webkit-builder [![NPM version][npm-image]][npm-url] [![Dependency Status][depstat-image]][depstat-url]

[![NPM](https://nodei.co/npm/grunt-node-webkit-builder.png?downloads=true)](https://nodei.co/npm/grunt-node-webkit-builder/)

> Let's you build your node-webkit apps for osx, win, and linux with grunt. It will download the prebuilt binaries for a specify version, unpacks it, creates a release folder, create the app.nw file for a specified directory and copys the app.nw file where it belongs.

*Issues with the output should be reported on the node-webkit-builder [issue tracker](https://github.com/mllrsohn/node-webkit-builder/issues).*

## Getting Started
This plugin requires Grunt `~0.4.1`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-node-webkit-builder --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-node-webkit-builder');
```

## The "nodewebkit" task


### Options

Exactly the same as https://github.com/mllrsohn/node-webkit-builder. You have the advantage to configure the files via grunt.


### Usage Examples

```js
grunt.initConfig({
  nodewebkit: {
    options: {
        platforms: ['win','osx'],
        buildDir: './webkitbuilds', // Where the build version of my node-webkit app is saved
    },
    src: ['./example/public/**/*'] // Your node-webkit app
  },
})
```

## Troubleshooting

### OSX ulimit

Darwin (OS X kernel) has a low limit for file descriptors (256 per process) by default, so you might get an `EMFILE` error or an error mentioning "too many open files" if youtry to open more file descriptors than this.

To get around it, run `ulimit -n 1024` (or add it to your `~/.bash_profile`). For more information, see [henvic/osx-ulimit](https://github.com/henvic/osx-ulimit).


## Release History
- 2014-08-01    `0.2.0` Moved logic into a separate [module](https://github.com/mllrsohn/node-webkit-builder), config options will be backward compatible except `keep_nw` is no longer supported
- 2013-09-19    Removed config merging (but kept the lookup for version number and name), added keep_nw option, fixed various small bugs.
- 2013-09-09    fixed accidential deletion of nw.exe on windows builds, adding several improvements, opt in for timestamped builds, using version and name from package.json to name the build product and build dir, renamed download directory to `cache`, added merge from package.json options for nodewebkit (no need to add configuration to Gruntfile, but stays optional)
- 2013-08-20    fix for the unzip lib
- 2013-08-13    initial release

[npm-url]: https://npmjs.org/package/grunt-node-webkit-builder
[npm-image]: http://img.shields.io/npm/v/grunt-node-webkit-builder.svg?style=flat

[depstat-url]: https://david-dm.org/mllrsohn/grunt-node-webkit-builder
[depstat-image]: https://david-dm.org/mllrsohn/grunt-node-webkit-builder.svg?style=flat
