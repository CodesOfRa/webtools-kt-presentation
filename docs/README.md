# Tools for modern web development 🛠

[[toc]]

## Linting tools

Linting tools analyse the code for potential errors , they can also enforce coding conventions to increase code quality.

**ESlint** is the dominant linting tool for JavaScript.

#### 💻 Exercise

Include ESlint as part of the project

```bash
npm install eslint --save-dev
```

Set up configuration file

```bash
./node_modules/.bin/eslint --init
```

Run ESlint on your project

```bash
npx eslint
```

::: tip
**Prettier** is another popular linting tool
:::

## Bundlers

Bundlers combine and optimize multiple modules/files into one or more production ready bundles.

### Webpack

It grabs all the app's files : JavaScript, CSS, images, fonts ... and create a big map of everything that's needed(dependency graph). From this it generates the bundler files.

What can you do with webpack

- hot module replacement
- lazy loading
- cashing

Things to know in order to configure Webpack :

- **Entry point** - Webpack needs to know what is the start file to build the dependency graph from
- **Output** - where Webpack should create the bundle(s) and what to call them
- **Loaders** - They just transform files. Webpack knows by default how to transform JavaScript, loaders tell it how to transform other types of files CSS, SCSS, images,SVGs
  - _"test"_ properties identify the files to transform
  - _"use"_ properties specify which loader to use
- **Plugins** - they can optimize bundlers, manage assets and injecting environment variables

:::tip
Basically everything is a plugin in Webpack
:::

#### 💻 Exercise

Install webpack

```bash
npm install webpack webpack-cli --save-dev
```

Then create the bundle by running

```bash
npx webpack
```

Create `webpack.config.js`

```javascript
const path = require('path');

module.exports = {
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'bundle.js'
  }
};
```

In `package.json` add

```json
...
"build":'webpack'
...

```

Add `CSS` loader

```javascript
module: {
  rules: [{test: /\.css$/, use: 'css-loader'}];
}
```

change the `webpack.config.js`

```javascript
const webpack = require('webpack')
...
plugins: [
    new webpack.ProgressPlugin()
  ]
```

Hot module replacement

```javascript
 devServer: {
      contentBase: './dist',
     hot: true
    }
 ...
 plugins:[ new webpack.HotModuleReplacementPlugin()]
```

⚠️ We'll come back to this example after talking about Transpilers

```bash
npm install -D babel-loader @babel/core @babel/preset-env webpack
```

```javascript
module: {
  rules: [
    {
      test: /\.m?js$/,
      exclude: /(node_modules|bower_components)/,
      use: {
        loader: 'babel-loader',
        options: {
          presets: ['@babel/preset-env']
        }
      }
    }
  ];
}
```

🐨 For more information check [Webpack](https://webpack.js.org/)

### Parcel

Similar with Webpack but it needs less configuration

#### 💻 Exercise

Install Parcel CLI:

```bash
npm install -g parcel-bundler
```

Create an index.html page

```html
<html>
  <body>
    <script src="./index.js"></script>
  </body>
</html>
```

Point the entry file for Parcel by running

```bash
parcel index.html
```

🐨 For more information check [Parcel](https://parceljs.org/)

## Transpilers

Transpilers convert one programming language into a new programming language with the same level of abstraction.
We want to use the latest syntax(eg ES6) but the browsers are not ready yet. Same applies for TypeScript.

A very popular transpiler is **Babel**

:::tip
Babel is a toolchain that is mainly used to convert ECMAScript 2015+ code into a backwards compatible version of JavaScript in current and older browsers or environments.
:::

#### 💻 Exercise

```bash
npm install --save-dev @babel/core @babel/cli
```

Then transpile the file, first install the arrow functions plugin

```bash
npm install --save-dev @babel/plugin-transform-arrow-functions
npx babel --plugins @babel/plugin-transform-arrow-functions src/index.js
```

You can also create a `babel.config.js` and add it to the `package.json`

```javascript
module.exports = function (api) {
  api.cache(true);

  const presets = [ ... ];
  const plugins = [ ... ];

  return {
    presets,
    plugins
  };
}
```

🐨 For more information check [Babel](https://babeljs.io/)

## 📚 Resources

- [Understanding Webpack from inside out](https://www.youtube.com/watch?v=gEBUU6QfVzk)
- [Configuring Babel 7](https://www.youtube.com/watch?v=Tv4n_3zETHc)
