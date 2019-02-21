# Tools for modern web development 🛠

[[toc]]

## Linting tools

Linting tools analyse the code for potential errors , they can also enforce coding conventions to increase code quality.

**ESlint** is the dominant linting tool for JavaScript.

#### 💻Exercise

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

Then transpile the file

```bash
babel index.js
```

🐨 For more information check [Babel](https://babeljs.io/)
