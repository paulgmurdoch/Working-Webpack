# A Working Example of Webpack

A Simple repo holding an example of Webpack working for both SASS/SCSS and JS compiling into single files. The way this webpack is configured stores the compiled files into a `build` folder.

## Start

To start we simple need to run the below code in your terminal

```shell
npm install
```

Once that is run node will proceed to install all the required files as per the below list:

* inline-manifest-webpack-plugin
* css-loader
* extract-text-webpack-plugin
* node-sass
* sass-loader
* webpack

There are specific versions that this works on due to updates causing issues

Once up and running, we can simply build the project and it will proceed to compile the code for us

```Shell
npm run build
```

## Webpack files

Here is our webpack file, note this is built for sass/scss compiling and not less:

```Javascript
var ExtractTextPlugin = require('extract-text-webpack-plugin');

module.exports = {
  entry: ['./src/js/app.js', './src/sass/app.scss'],
  output: {
    filename: 'build/final.js'
  },
  module: {

    rules: [
      { // sass / scss loader for webpack
        test: /\.(sass|scss)$/,
        loader: ExtractTextPlugin.extract(['css-loader', 'sass-loader'])
      }
    ]
  },
  plugins: [
    new ExtractTextPlugin({ // define where to save the file
      filename: 'build/final.css',
      allChunks: true,
    }),
  ],
};
```