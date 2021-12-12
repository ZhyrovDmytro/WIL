# Adding TS to JS project

Install ts

```
npm install -D typescript
yarn add -D typescript
```

add ts config file **tsconfig.json**

```
tsc --init

// example 
{
  "compilerOptions": {
    "outDir": "./built",
    "allowJs": true,
    "target": "es5"
  },
  "include": ["./src/**/*"]
}
```

specifying a few things to TypeScript:

1. Read in any files it understands in the `src` directory (with [`include`](https://www.typescriptlang.org/tsconfig#include)).
2. Accept JavaScript files as inputs (with [`allowJs`](https://www.typescriptlang.org/tsconfig#allowJs)).
3. Emit all of the output files in `built` (with [`outDir`](https://www.typescriptlang.org/tsconfig#outDir)).
4. Translate newer JavaScript constructs down to an older version like ECMAScript 5 (using [`target`](https://www.typescriptlang.org/tsconfig#target)).

### TS with Gulp

install gulp-typescript

```
npm install --save-dev gulp-typescript
```

create gulp file

```
var gulp = require("gulp");
var ts = require("gulp-typescript");
var tsProject = ts.createProject("tsconfig.json");
gulp.task("default", function () {
  return tsProject.src().pipe(tsProject()).js.pipe(gulp.dest("dist"));
});
```

### TS with Webpack

install ts-loader

```
npm install ts-loader source-map-loader
```

edit webpack config

```
module.exports = {
  entry: "./src/index.ts",
  output: {
    filename: "./dist/bundle.js",
  },
  // Enable sourcemaps for debugging webpack's output.
  devtool: "source-map",
  resolve: {
    // Add '.ts' and '.tsx' as resolvable extensions.
    extensions: ["", ".webpack.js", ".web.js", ".ts", ".tsx", ".js"],
  },
  module: {
    rules: [
      // All files with a '.ts' or '.tsx' extension will be handled by 'ts-loader'.
      { test: /\.tsx?$/, loader: "ts-loader" },
      // All output '.js' files will have any sourcemaps re-processed by 'source-map-loader'.
      { test: /\.js$/, loader: "source-map-loader" },
    ],
  },
  // Other options...
};
```

**ts-loader will need to run before any other loader that deals with `.js` files.**

****

Move .js files to .ts
