# Task automation with gulp

## Introduction

This document will serve as a reference to process automation with gulp.

## Gulp Installation

- [ ] Install gulp globally `npm install --global gulp-cli`
- [ ] In root of project, `npm install --save-dev gulp`
- [ ] `touch gulpfile.js`
- [ ] Open file and paste starter template

```
var gulp = require('gulp');

gulp.task('default', function() {
  // place code for your default task here
});

```

- [ ] run `gulp` to test. The file should run without errors.

## Running Multiple Tasks

- By default, running `gulp` will execute only the 'default' task.
- Multiple tasks can be chained as illustrated bellow:

```
gulp.task('default', ['<task1>', ''<task2>'']);
```
## Minify CSS

- [ ] Run `npm install gulp-clean-css --save-dev` [source](https://github.com/scniro/gulp-clean-css)
- [ ] Move your css files to an assets folder (ex: assets/stylesheets)
- [ ] Use the following code to minify css files and place them in the specified destination:

```
let gulp = require('gulp');
let cleanCSS = require('gulp-clean-css');

gulp.task('default', () => {
    return gulp.src('assets/stylesheets/*.css')
        .pipe(cleanCSS())
        .pipe(gulp.dest('stylesheets'));
});

```

## Uglify JS

Checkout out the [guide](https://codehangar.io/concatenate-and-minify-javascript-with-gulp/)

- [ ] Run `npm install --save-dev gulp-uglify` [source](https://github.com/terinjokes/gulp-uglify)
- [ ] Run `npm install --save-dev gulp-rename` [source](https://github.com/hparra/gulp-rename)
- [ ] Move your javascript files to an assets folder (ex: assets/javascripts)
- [ ] Use the following code to minify js files and place them in the specified destination:

```

gulp.task('uglify', function() {
    return gulp.src('assets/javascripts/**/*.js')
        .pipe(uglify())
        .pipe(rename({extname: ".min.js"}))
        .pipe(gulp.dest('javascripts'));
});

```

## Optimize images

- Run `npm install --save-dev gulp-imagemin` [source](https://github.com/sindresorhus/gulp-imagemin)

```
`gulp.task('imagin', () =>
gulp.src('assets/images/*')
    .pipe(imagemin())
    .pipe(gulp.dest('dist/images'))
);

```

## Complete example

- As an example, the gulpfile for "The user is drunk" is bellow:

```
let gulp = require('gulp');
let cleanCSS = require('gulp-clean-css');
let uglify = require('gulp-uglify');
let rename = require('gulp-rename');
let imagemin = require('gulp-imagemin');

gulp.task('minify-css', () => {
    return gulp.src('assets/stylesheets/*.css')
        .pipe(cleanCSS())
        .pipe(gulp.dest('stylesheets'));
});

gulp.task('uglify', function() {
    return gulp.src('assets/javascripts/**/*.js')
        .pipe(uglify())
        .pipe(rename({extname: ".min.js"}))
        .pipe(gulp.dest('javascripts'));
});

gulp.task('imagin', () =>
gulp.src('assets/images/*')
    .pipe(imagemin())
    .pipe(gulp.dest('stylesheets'))
);

gulp.task('default', ['minify-css', 'uglify', 'imagin']);

```
