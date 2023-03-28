# Gulp 打包器

## 实例

​    <b>在使用实例之前需要先下载插件:</b> 

```node
yarn add gulp 
```



   <b>完成后的 package.json 样式:</b> 

```json
{
    name: 'xxx',
    "version": "1.0.0",
    "main": "xxx.js",
    "license": "MIT",
    "devDependencies": {
        "babel-core": "^6.26.3",
        "babel-preset-env": "^1.7.0",
        "browser-sync": "^2.27.11",
        "del": "6.0.0",
        "gulp": "^4.0.2",
        "gulp-autoprefixer": "^8.0.0",
        "gulp-babel": "^7.0.1",
        "gulp-clean-css": "^4.3.0",
        "gulp-imagemin": "^7.1.0",
        "gulp-notify": "^4.0.0",
        "gulp-plumber": "^1.2.1",
        "gulp-rename": "^2.0.0",
        "gulp-sass": "^5.1.0",
        "gulp-uglify": "^3.0.2",
        "html-minifier": "^4.0.0",
        "sass": "^1.58.1"
  }
}
```



```js
// 导入 del 删除模块
const del = require('del');

// 导入 命名 模块
const rename = require('gulp-rename');

// 导入 gulp 模块
const { src, dest, parallel, series, watch } = require('gulp');

// 导入 gulp 生态系统中的其他模块

// error 模块
const plumber = require('gulp-plumber');
const notify = require('gulp-notify');

// todo: HTML 模块
const minify = require('html-minifier').minify;

// todo: CSS 模块
const sass = require('gulp-sass')(require('sass'));
const cleanCss = require('gulp-clean-css');
const autoprefixer = require('gulp-autoprefixer');

// todo: JS 模块
const babel = require('gulp-babel');
const uglify = require('gulp-uglify');

// todo: image 模块
const imagemin = require('gulp-imagemin');

// todo: server 模块
const create = require('browser-sync').create();


// 声明错误处理函数
const throwError = (error) => {
    notify.onError({
        title: 'Glup compile error!',
        subtitle: 'throw new Error!',
        message: 'Error: <%= error.message %>',
        sound: 'Pop'
    })(error);

    this.emit('end');
}

// 声明 HTML 处理任务
const delHTML = {
    collapseWhitespace: true,
    collapseBooleanAttributes: true,
    removeComments: true,
    removeEmptyAttributes: true,
    removeScriptTypeAttributes: true,
    removeStyleLinkTypeAttributes: true,
    minifyJs: true,
    minifyCss: true
}

// 声明 HTML 任务
const configHTML = () => {
    return src('src/index.html', { base: 'src' })
        .on('data', (file) => {
            const compileFile = Buffer.from(
                minify(file.contents.toString(), delHTML))
                return file.contents = compileFile
        })
        .pipe(dest('dist'))
}

// 声明 HTML
const HTML = series(configHTML);

// 声明 style 任务
const style = () => {
    return src('./src/scss/index.scss')
        .pipe(plumber({errorHandler: throwError}))
        .pipe(sass().on('error', sass.logError))
        .pipe(autoprefixer())
        .pipe(cleanCss())
        .pipe(rename({ extname: '.min.css' }))
        .pipe(dest('./dist/css')
    )
}

// 声明 script 任务
const script = () => {
    return src('src/js/*.js', { base: 'src' })
        .pipe(plumber({errorHandler: throwError}))
        .pipe(babel({
            presets: ['babel-preset-env']
        }))
        .pipe(uglify())
        .pipe(rename({ extname: '.min.js' }))
        .pipe(dest('dist'))
}

// 声明 image 任务
const image = () => {
    return src('src/assets/images/**', { base: 'src' })
        .pipe(imagemin([
            imagemin.gifsicle({ interlaced: true }),
            imagemin.mozjpeg({ quality: 80, progressive: true }),
            imagemin.optipng({ optimizationLevel: 5 }),
            imagemin.svgo({
                plugins: [
                    { removeViewBox: true },
                    { cleanupIDs: false }
                ]
            })
        ]))
        .pipe(dest('dist'))
}

// 声明一个转移任务 - video
const transferVideo = () => {
    return src('src/assets/videos/**', { base: 'src' })
        .pipe(dest('dist'))
}

// 设置 transferVideo 的别名
const video = transferVideo;

// 声明一个转移任务 - lib ( 第三方库 )
const transferLib = () => {
    return src('src/lib/**', { base: 'src' })
        .pipe(dest('dist'))
}

// 设置 transferLib 的别名
const lib = transferLib;

// 设置一个转移任务 - font
const transferFont = () => {
    return src('src/fonts/**', { base: 'src' })
        .pipe(dest('dist'))
}

// 设置 transferFont 的别名
const font = transferFont;


// 删除 dist 目录
const clean = () => {
    return del(['dist'])
}

// 声明 serve 任务 ( 启动服务 )
const server = () => {
    watch('./src/**', parallel(HTML, style, script));
    create.init({
        notify: false,
        server: {
            baseDir: './dist',
            routes: {
                '/node_modules': 'node_modules'
            }
        },
        port: 8080,
        open: true,
        files: 'dist/**'
    });
}

// 声明并行任务
const build = parallel(HTML, style, script, image, video, lib, font);

// 声明串行任务
const dev = series(clean, build)

// 声明启动任务
const start = series(dev, server);

// 导出任务
module.exports = {
    HTML,
    style,
    script,
    image,
    video,
    lib,
    font,
    clean,
    server,
    build,
    dev,
    default: start
}
```

