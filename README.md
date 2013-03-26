# grunt-cafe-mocha

> A Grunt plugin for running server-side Mocha tests that actually works.

## Getting Started
This plugin requires Grunt `~0.4.1`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-cafe-mocha --save-dev
```

One the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-cafe-mocha');
```

## The "cafemocha" task

### Overview
In your project's Gruntfile, add a section named `cafemocha` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  cafemocha: {
    testThis: {
        src: 'test/this/**/*.js',
        options: {
            ui: 'bdd',
            require: [
                'should',
            ],
        },
    },

    /// Any number of tests here...

    testThat: {
        src: 'test/that/*.js',
        options: {
            ui: 'tdd',
            growl: true,
            reporter: 'nyan',
        },
    },
  },
})
```

### Options

#### options.require
Type: `List`

Default value: `[]`

A list of modules to load before running the tests.

#### options.reporter
Type: `String`

Default value: `'list'`

A string value to pick which reporter to use when testing. To see a list of all
the reporters, check [here](http://visionmedia.github.com/mocha/#reporters).

#### options.ui
Type: `String`

Default value: `'bdd'`

A string value to pick which type of user-interface to use. The options are
`bdd`, `tdd`, or `exports`. Read more about interfaces
[here](http://visionmedia.github.com/mocha/#interfaces).

#### options.grep
Type: `String` to be turned into a `RegExp`

Default value: `.*`

A string value to run tests that only match the given pattern. For example, if
the Mocha test file has the tests: `test1`, `test2`, `test3`, `test4`, if
`options.grep = 'test[12]'`, it will only match the first two tests and run
them.

#### options.invert
Type: `Boolean`

Default value: `false`

Either `true` or `false` that will either match invert the matching. Using the
example from the section for **options.grep**, setting this option to `true`
would result in the *last* two tests being ran, but not the first two.

#### options.timeout
Type: `Integer`

Default value: `2000`

The tiemout time for a test-case in milliseconds.

#### options.slow
Type: `Integer`

Default value: `2000`

Threshold for a "slow" test in milliseconds.

#### options.colors
Type: `Boolean`

Default value: `undefined`

True forces the enabling of colors while false forces the disabling of colors.

#### options.growl
Type: `Boolean`

Default value: `false`

Enable Growl/OS X (10.8) notification system on test completion.

#### options.bail
Type: `Boolean`

Default value: `false`

Bail after the first test failure.

#### options.globals
Type: `List`

Default value: `[]`

A list of globals names.

#### options.ignoreLeaks
Type: `List`

Default value: `false`

Ignore global variable leaks

### Usage Examples

#### Basic Behavioral-driven Development

```js
grunt.initConfig({
  cafemocha: {
    src: 'test/**/*.js',
    options: {
        ui: 'bdd',
    },
  },
})
```

#### Basic Test-driven Development

```js
grunt.initConfig({
    cafemocha: {
        src: 'test/**/*.js',
        options: {
            ui: 'tdd',
        },
    },
});
```

#### Require More Modules

```js
grunt.initConfig({
    cafemocha: {
        options: {
            require: ['should', 'something', 'else', 'here'];
        },
        src: 'test/**/*.js'
    },
});
```

#### More Tests

```js
grunt.initConfig({
    cafemocha: {
        foo: {
            src: 'test/foo/*.js',
            options: {
                ui: 'tdd',
            },
        },

        bar: {
            src: 'test/bar/*.js',
            options: {
                ui: 'bdd',
            },
        },
    },
});
```

## Contributing
Feel free to fork it and add as you please. If you add a particularly nice
feature, send me a pull request. I'd love to improve it.

### Todo List
* Support the `--compilers` option in Mocha
* Support the watching of files for changes
