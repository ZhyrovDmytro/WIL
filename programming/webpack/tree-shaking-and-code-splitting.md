# Tree shaking and code splitting

**Tree shaking -** dead code elimination, emoving of unused code in the production build.

**Code splitting -** split production code into more small modules that are loaded on demand.

Webpack supports tree-shaking and it uses **babel-preset-env package**. This package bundles the files and transforms them back to **CommonJS modules**.

Use Tree

```text
// webpack.config.js 
const HtmlWebPackPlugin = require('html-webpack-plugin'); 
```

```text
module.exports = { 
  module: { 
    rules: [ 
      { 
        test: /\.(js|jsx)$/, 
        exclude: /node_modules/, 
        use: { 
          loader: babel-loader, 
          /* This configuration aids babel-preset-env to disable transpiling of import or export modules to commonJS */ 
          options: { 
            presets: [ 
              [ 'es2015', { modules: false }] 
            ] 
          } 
        } 
      } 
    ] 
  }, 
  plugin: [ new HtmlWebPackPlugin ({  
    template: './src/index.html', 
    fileName: './index.html' 
  }); 
} 
```

Take care of **side effects**. It is only visible when a function or expression modifies a state outside its context. The common examples of side effects include making a call to API, manipulating the DOM, or writing to a DB.

Make webpack aware of side effects:

```text
// package.json 
{ 
  "name": "Tree Shaking Project", 
  "side-effects": false 
} 
```

in case if you want to apply side effects for specific file:

```text
// package.json 
{ 
  "name": "Tree Shaking Project", 
  "side-effects": false,  
  // when you want to notify webpack of files with side-effects. 
  "side-effects": [  
    "name-of-file.js" 
  ] 
} 
```

Similarly, configure in webpack.config.json

```text
// webpack.config.json 
module.exports = { 
  modules: { 
    rules: [ 
      { 
        test: /\.(js|jsx)$/, 
        exclude: /node_modules/, 
        use: { 
          loader: babel-loader,           
          side-effects: false  
        } 
      } 
    ] 
  } 
} 
```

**Some rules to follow:**

* Configure the webpack option to ignore transpiling modules to CommonJS.
* Use ES2015 module syntax \(i.e. import and export\).
* Configure the side effects property option in package.json file of the project

sources:

* [https://medium.com/@craigmiller160/how-to-fully-optimize-webpack-4-tree-shaking-405e1c76038](https://medium.com/@craigmiller160/how-to-fully-optimize-webpack-4-tree-shaking-405e1c76038)

