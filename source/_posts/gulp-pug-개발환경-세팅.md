---
title: gulp-pug 개발환경 세팅
date: 2017-09-18 16:57:45
tags:
---


vue 프레임워크 없이 pug를 사용하려 했더니 Gulp를 써야했다.
그래서 pug watch를 하고, HTML을 minify 하지 않도록 개발환경 세팅을 했다.


```javascript
var gulp = require('gulp');
var pug = require('gulp-pug');

gulp.task('pug', function () {
  gulp.src('./src/*.pug')
  .pipe(pug({
    pretty: true
  }))
  .pipe(gulp.dest('./dist'))
})

gulp.task('watch', function () {
  gulp.watch('src/*.pug', ['pug'])
})

gulp.task('default', ['pug', 'watch']);
```
