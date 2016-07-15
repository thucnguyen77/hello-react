# hello-react
My first React sample

## Basic steps to initialize a simple React-based app
Make sure [NodeJS](https://nodejs.org/) is already installed in your machine.

### Create project folder structure
```sh
mkdir hello-react
cd hello-react
mkdir app
mkdir public
```
### Initialize the project manifest
```sh
npm init
```
### Install necessary Webpack and Babel modules
```
npm install --save-dev webpack
npm install --save-dev webpack-dev-server

npm install --save-dev babel-core
npm install --save-dev babel-loader

npm install --save-dev babel-preset-es2015
npm install --save-dev babel-preset-react
```
### Install React modules
```
npm install --save react
npm install --save react-dom
```
### Start coding now
- Create `index.html` file in `public` folder and add following lines of code
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8"/>
        <title> My first React app</title>
    </head>
    <body>
        <div id="app"></div>
        <script src="index.js"></script>
    </body>
</html>
```
- Create `hello.jsx` file in `app` folder and add following lines of code
```jsx
import React from 'react';
import ReactDOM from 'react-dom';
 
class Hello extends React.Component {
  render() {
    return <h1>Hello React</h1>
  }
}

ReactDOM.render(<Hello/>, document.getElementById('app'));
```
- Create a `main.js` file in `app` folder and add following lines of code
```
import Hello from './hello.jsx';
```
### Configure Webpack
- Create a `webpack.config.js` file in root folder
- Add following lines to `webpack.config.js` file

```
module.exports = {
  devtool: 'eval-source-map',

  entry:  __dirname + "/app/main.js",
  output: {
    path: __dirname + "/public",
    filename: "index.js"
  },

  module: {
    loaders: [
      {
        test: /\.json$/,
        loader: "json"
      },
      {
        test: /\.jsx?$/,
        exclude: /node_modules/,
        loader: 'babel',
        query: {
          presets: ['es2015','react']
        }
      }
    ]
  },

  devServer: {
    contentBase: "./public",
    colors: true,
    historyApiFallback: true,
    inline: true
  }
}
```
### Run the app now
- Go back to command prompt window and run following command.
```
webpack-dev-server --progress --colors
```
- Open browser and go to http://localhost:8080/. The greeting message should be there.

### Next steps
Given the ultimate goal is to build an actual SPA, following steps are put on the road map.
- Put on an elegant UI such as [Material-UI](http://www.material-ui.com/).
- Integrate with Redux
- Integrate with back-end ASP.NET Web API
- ...
