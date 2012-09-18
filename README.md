Automatically run *client-side* mocha specs via grunt/mocha/PhantomJS

For a grunt task for server-side mocha tests, see https://github.com/yaymukund/grunt-simple-mocha

# grunt-mocha

(package/README format heavily borrowed from [grunt-jasmine-task](hhttps://github.com/creynders/grunt-jasmine-task) and builtin QUnit task)

[Grunt](https://github.com/cowboy/grunt) plugin for running Mocha browser specs in a headless browser (PhantomJS)

## Getting Started

### Vanilla JS

- Write mocha task description in grunt config using full format and specify `run: true` option (see `example/grunt.js` for details);
- Check for PhantomJS `userAgent` in a test html file and run tests only in a real browser (see `example/test/test2.html` for details).

In this case you shouldn't include `mocha-helper.js` (it will be included automatically) and tests will be run from `mocha-helper.js`.

Alternatively, include `mocha-helper.js` from `tasks/mocha` after you include `mocha.js` and run `mocha.setup` in your HTML file. The helper will override `mocha.setup` if it detects PhantomJS. See `exampletest/test.html`.

### AMD

Example setup with AMD (advanced): https://gist.github.com/2655876

### Grunt and this plugin

First, make sure you have grunt installed globally, `npm install grunt -g`

Install this grunt plugin next to your project's [grunt.js gruntfile](https://github.com/cowboy/grunt/blob/master/docs/getting_started.md) with: `npm install grunt-mocha`

Then add this line to your project's `grunt.js` gruntfile at the bottom:

```javascript
grunt.loadNpmTasks('grunt-mocha');
```

Also add this to the ```grunt.initConfig``` object in the same file:

```javascript
mocha: {
  index: ['specs/index.html']
},
```

Replace ```specs/index.html``` with the location of your mocha spec running html file.

Now you can run the mocha task with `grunt mocha`, but it won't work. That's because you need...

### PhantomJS

This task is for running Mocha tests in a headless browser, PhantomJS. [See the FAQ on how to install PhantomJS](https://github.com/cowboy/grunt/blob/master/docs/faq.md#why-does-grunt-complain-that-phantomjs-isnt-installed).

### Mocha

Use [Mocha](http://visionmedia.github.com/mocha/)

### Maybe Growl?

Growl support is optional. I'm not sure what the Windows situation is with growl.

### Hacks

The PhantomJS -> Grunt superdimensional conduit uses `alert`. If you have disabled or aliased alert in your app, this won't work. I have conveniently set a global `PHANTOMJS` on `window` so you can conditionally override alert in your app.

## License
Copyright (c) 2012 Kelly Miyashiro
Licensed under the MIT license.