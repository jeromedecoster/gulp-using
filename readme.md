# gulp-using

<a href="http://gulpjs.com" target="_blank">Gulp</a> filter. Lists all files used. Helps you to verify what your patterns catch

## Install

Install with <a href="https://npmjs.org/package/gulp-using" target="_blank">npm</a>

```
npm install --save-dev gulp-using
```

## Example

After some complex `src` patterns, and some added filter plugins, it helps you to list all files catched

```js
var using = require('gulp-using');

var jsfiles = ['./src/js/**/*.js', '!./src/js/vendor/**'];

gulp.task('default', function() {
  gulp.watch(jsfiles, function() {
    gulp.src(jsfiles)
      // action or filter...
      .pipe(using())
      // ...
  });
});
```

Output:

```
[gulp] Running 'default'...
[gulp] Finished 'default' in 14 ms
[gulp] Using file ./src/js/index.js
[gulp] Using file ./src/js/multiply.js
[gulp] Using file ./src/js/square.js
```

## Options

#### options.path

* Type: `String`
* Default: `cwd`
* Values: `cwd`, `path`, `relative`

How the file path is displayed

#### options.color

* Type: `String`
* Default: `magenta`
* Values: `black`, `blue`, `cyan`, `gray`, `green`, `magenta`, `red`, `white`, `yellow`

How the file path is colored

#### options.prefix

* Type: `String`
* Default: `Using file`

Message shown before the file path

```js
// ...
.pipe(using({prefix:'Using', path:'relative', color:'blue'}))
```

Output:

```
[gulp] Running 'default'...
[gulp] Finished 'default' in 14 ms
[gulp] Using index.js
[gulp] Using multiply.js
[gulp] Using square.js
```
