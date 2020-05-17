## How to create a hello world Reactjs app

```
npm init -y
npm i react react-dom
npm i webpack webpack-cli webpack-dev-server html-webpack-plugin html-loader @babel/core babel-loader @babel/preset-env @babel/preset-react --save-dev
```

### add in package.json inside "scripts"
```
"start": "webpack-dev-server --open --mode development",
"build": "webpack --mode production"
```

### .babelrc
```
{
  "presets": ["@babel/preset-env", "@babel/preset-react"]
}
```

### webpack.config.js
```
const HtmlWebPackPlugin = require("html-webpack-plugin");

module.exports = {
  entry: ['./src/index.js'],
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: {
          loader: "babel-loader"
        }
      },
      {
        test: /\.html$/,
        use: [
          {
            loader: "html-loader"
          }
        ]
      }
    ]
  },
  plugins: [
    new HtmlWebPackPlugin({
      template: "./src/index.html",
      filename: "./index.html"
    })
  ]
};
```

### src/index.html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <title>React App</title>
</head>
<body>
    <div id="container"></div>
</body>
</html>
```

### src/index.js
```
import React from 'react';
import ReactDOM from 'react-dom';
import App from './app';

ReactDOM.render(<App />, document.getElementById("container"));
```

### src/app.js
```
import React from 'react';

const App = () => {
  return <h1>
    Welcome to Reactjs!
  </h1>
}

export default App;
```

### How to run
```
npm install
npm start
```