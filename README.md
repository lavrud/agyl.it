# Loquax TI



* npm install -g bower

* bower install bootstrap-sass --save-dev

* bower install breakpoint-sass --save-dev

* bower install fontawesome --save-dev

* bower install wowjs --save-dev

* criar arquivo .gitignore > inserir pasta (bower_components)

* bower init

* npm init

* npm install -g gulp 

* npm install gulp --save-dev

* npm install gulp-sass --save-dev

* npm install gulp-uglify --save-dev

* npm install gulp-htmlmin --save-dev

* npm install gulp-watch --save-dev

* npm install -g live-server

* arquivo .gitignore > inserir pasta (node_modules)

* npm ls > npm ls --depth=0

* criar pasta 
	*sass > (style.sass / plugins.sass)
	*templates > (_style.sass)

* criar pasta css > (comando gulp renderiza sass p/css)

* rodar gulp e live-server em cmd

/* gulpfile.js */ 

var gulp = require('gulp');
var sass = require('gulp-sass');
var uglify = require("gulp-uglify");
var htmlmin = require('gulp-htmlmin');
var watch = require('gulp-watch');

// task sass renderizar/comprimir/css
gulp.task('sass', function () {
    return gulp.src('scss/**/*.scss').pipe(sass({
        outputStyle: 'compressed'
    }).on('error', sass.logError)).pipe(gulp.dest('css'));
});
// task minify comprimir/js
gulp.task('min-js', function () {
    gulp.src('js/**/*.js').pipe(uglify()).pipe(gulp.dest('js'));
});
// task html-minify comprimir/html
gulp.task('min-html', function () {
    gulp.src('index.html').pipe(htmlmin({
        collapseWhitespace: true
    })).pipe(gulp.dest('html'));
});
// task watch assistir tarefas gulp
gulp.task('watch', function () {
    gulp.watch('scss/**/*.scss', ['sass']);
});
// task padrão gulp
gulp.task('default', ['sass', 'min-js', 'min-html', 'watch']);



--------------------------------------------------------------

/* CSS */

<link rel="stylesheet" href="css/plugins.css">
<link rel="stylesheet" href="css/style.css">

--------------------------------------------------------------

/* SCRIPTS */

<!-- jQuery (necessary for Bootstrap's JavaScript plugins) -->
<script src="bower_components/jquery/dist/jquery.min.js"></script>
    <!-- Animate WOW Scrolling -->
<script src="bower_components/wow/dist/wow.min.js"></script>
    <script>
        new WOW().init();
    </script>
    <!-- Google Analytics: change UA-XXXXX-X to be your site's ID. -->
    <script>
        (function(b, o, i, l, e, r) {
            b.GoogleAnalyticsObject = l;
            b[l] || (b[l] = function() {
                (b[l].q = b[l].q || []).push(arguments)
            });
            b[l].l = +new Date;
            e = o.createElement(i);
            r = o.getElementsByTagName(i)[0];
            e.src = '//www.google-analytics.com/analytics.js';
            r.parentNode.insertBefore(e, r)
        }(window, document, 'script', 'ga'));
        ga('create', 'UA-XXXXX-X');
        ga('send', 'pageview');

    </script>

gulp PHP

// Gulp 3.8 code... differs in 4.0
var gulp = require('gulp'),
    php = require('gulp-connect-php'),
    browserSync = require('browser-sync');

var reload  = browserSync.reload;

gulp.task('php', function() {
    php.server({ base: 'build', port: 8010, keepalive: true});
});
gulp.task('browser-sync',['php'], function() {
    browserSync.init({
        proxy: '127.0.0.1:8010',
        port: 8080,
        open: true,
        notify: false
    });
});
gulp.task('default', ['browser-sync'], function () {
    gulp.watch(['build/*.php'], [reload]);
});











"# agyl.it" 
