# webpack 2

```sh
$ npm i -D css-loader style-loader extract-text-webpack-plugin


```

## CSS (.scss)


```sh
$ npm i -D css-loader style-loader

$ npm i -D extract-text-webpack-plugin
```


> webpack.config.js

```js

module.exports = {
    module: {
        rules: [{
            test: /\.css$/,
            use: [ 'style-loader', 'css-loader' ]
        }]
    }
}

```


### `ExtractTextWebpackPlugin`

```sh

$ npm i -D extract-text-webpack-plugin
```


```js

const ExtractTextPlugin = require('extract-text-webpack-plugin');

module.exports = {
    module: {
        rules: [{
            test: /\.css$/,
            use: ExtractTextPlugin.extract({
                use: 'css-loader'
            })
        }]
    },
    plugins: [
        new ExtractTextPlugin('styles.css')
    ]
}

```


















