# webpack 2



## CSS (.scss)


```sh
$ npm i -D css-loader style-loader

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








