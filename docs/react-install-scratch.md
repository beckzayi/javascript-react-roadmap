## Install React and Webpack from scratch

`npx create-react-app` provides a simple way to create React app. If interested, we can create it from scratch and see what is inside.

Below are only brief steps.

1. npm init -y
2. mkdir dist
3. touch index.html (in dist folder)
4. mkdir src, and touch index.js (in src folder)
5. cd .. (cd to the project root folder)
6. `npm install --save-dev webpack webpack-dev-server webpack-cli`
7. package.json, "scripts": "start": `"webpack-dev-server --config ./webpack.config.js --mode development"`  ---- it means config use the webpack.config.js file and use development mode
8. touch webpack.config.js (in root folder)
9. webpack.config.js - set up `entry`, `output`, `devServer`
10. Add something in src/index.js
11. To start and test the server: npm start
12. See the message on command line, should able to open http://localhost:8080
13. Set up babel in Webpack. Babel is used to transpile ES6 to ES5.
`npm install --save-dev babel-core@^6 babel-loader@^7 babel-preset-env` (babel-core v6, babel-loader v7)
`babel-loader` : it compiles code. It takes code to babel compiler.
`babel-preset-env` : checks the features that have implemented on browser
`npm install --save-dev babel-preset-stage-2`
`npm install --save-dev babel-preset-react`
14. In package.json: `"babel": { "presets": ["env", "stage-2", "react"] }`
15. In webpack.config.js, `module: { rules: [ { test: /\.(js|jsx)$/, exclude: /node_modules/, use: ['babel-loader'] } ] }, resolve: { extensions: ['.js', '.jsx'] }`
16. npm install --save react react-dom
17. You may install `eslint` and `eslint-loader` if necessary. In webpack.config.js, module rules, add `{ test: /\.(js|jsx)$/, exclude: /node_modules/, use: ['eslink-loader'] }`

