# Tools for modern web development 

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
 ### Webpack
  [Webpack](https://webpack.js.org/)
 ### Parcel
  [Parcel](https://parceljs.org/)
 ## Transpilers
 Transpilers convert one programming language into a new programming language with the same level of abstraction.
We want to use the latest syntax(eg ES6) but the browsers are not ready yet. Same applies for TypeScript.

A very popular transpiler is  **Babel**