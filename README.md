# Wildbit-specific config for postcss-sorting

Sorts CSS properties in the order expected by [stylelint-config-wildbit](https://github.com/wildbit/stylelint-config-wildbit).

## How to use

1) Install dependencies:

```
npm install --save-dev postcss-scss postcss-sorting
```

2) Update `gulpfile.js`:

```js
var sorting = require('postcss-sorting');
var sortingConfig = require('scss-sorting.json');

gulp.task('cleanup', function () {
  return gulp.src(paths.styles.src + '**/*.scss')
    .pipe(
      postcss(
        [
          sorting(sortingConfig)
        ],
        {
          syntax: require('postcss-scss')
        }
      )
    )
    .pipe(gulp.dest(paths.styles.src));
});
```

3) Add to NPM scripts in `package.json`:

```json
  "scripts": {
    "cleanup": "gulp cleanup"
  }
```

4) Run:

```
npm run cleanup
```
