#  BrowserSync 

## BrowserSync提供了一种在多个浏览器里测试网页的很好方式

BrowserSync不需要使用浏览器插件，因为它本身就可以为你提供文件服务（如果文件是动态的，则为他们提供代理服务） 
和用来开启浏览器和服务器之间的socket的脚本服务。 
到目前为止这个功能的使用都十分顺畅。

[BrowserSync](http://www.w3ctech.com/topic/134)

```sh
$ npm install --save-dev browser-sync
``` 

```code
var gulp = require('gulp'),
    browserSync = require('browser-sync');

gulp.task('browser-sync', function () {
   var files = [
      'app/**/*.html',
      'app/assets/css/**/*.css',
      'app/assets/imgs/**/*.png',
      'app/assets/js/**/*.js'
   ];

   browserSync.init(files, {
      server: {
         baseDir: './app'
      }
   });
});
``` 


```js
var gulp = require('gulp'),
    jade = require('gulp-jade'),
    browserify = require('gulp-browserify'),
    uglify= require('gulp-uglify'),
    gulpif= require('gulp-if'),
    sass= require('gulp-sass'),
    browserSync = require('browser-sync'),
    connect= require('gulp-connect');
    
    
//watcher of html and all files
gulp.task('browser-sync', function () {
   var files = [
      'builds/html/**/*.html',
      'builds/css/**/*.css',
      'builds/assets/images/**/*.jpg',
      'builds/js/**/*.js'
   ];

   browserSync.init(files, {
      server: {
         baseDir: './builds'
      }
   });
});


gulp.task('watch',function(){
    gulp.watch('src/template/**/*.jade',['jade']);
    gulp.watch('src/js/**/*.js',['js']);
    gulp.watch('src/sass/**/*.scss',['sass']);
    gulp.watch('src/html/*.html',['browser-sync']);
});

gulp.task('default',['js','sass','jade','browser-sync','watch','connect']);
``` 





