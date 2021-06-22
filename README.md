# ⚠️ Deprecated, as now [stylelint-config-wildbit](https://github.com/wildbit/stylelint-config-wildbit) relies on `stylelint-order` plugin.

# Wildbit-specific config for postcss-sorting

Sorts CSS properties in the order expected by [stylelint-config-wildbit](https://github.com/wildbit/stylelint-config-wildbit).

## How to use

1) Install dependencies:

```
npm install --save-dev postcss-scss postcss-sorting
npm install --save-dev wildbit/postcss-sorting-config-wildbit
```

2) Update `gulpfile.js`:

```js
var sorting = require('postcss-sorting');
var sortingConfig = require('./node_modules/postcss-sorting-config-wildbit/scss-sorting.json');

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

4) Use correct media query @includes at your project:

```json
    [
      "@include retina",
      "@include mobile",
      "@include tablet",
      "@include desktop"
    ]
```


5) Run:

```
npm run cleanup
```
