## 通过 gulp 设置css,html,js文件修改自动加载到浏览器
```

var gulp = require('gulp');
var browsersync = require("browser-sync").create();

// startup server
gulp.task('build-server', function (done) {
  browsersync.init({
      server: {
          baseDir: "./app"
      }
  });
  done();
  console.log('Server was launched');
});

// browser reload 
gulp.task('browser-reload', function (done){
  browsersync.reload();
  done();
  console.log('Browser reload completed');
});

// watch files
gulp.task('watch-files', function(done) {
  gulp.watch("app/*/*.html", gulp.task('browser-reload'));
  gulp.watch("app/*/*.css", gulp.task('browser-reload'));
  gulp.watch("app/*/*.js", gulp.task('browser-reload'));
  done();
  console.log(('gulp watch started'));
});

// task
gulp.task('default', gulp.series('build-server', 'watch-files', function(done){
  done();
  console.log('Default all task done!');
}));

```
> [Server with live-reloading and CSS injection](https://github.com/gulpjs/gulp/blob/master/docs/recipes/server-with-livereload-and-css-injection.md)


