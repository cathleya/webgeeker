# Errors & OK  
https://github.com/babel/babel.github.io/pull/958

## the error codes created by docs!

```js
'console.log([1, 2, 3].map(n = + 1)); '
``` 

```json
'{ "presets": ["es2015"] }' 
``` 

# After I modify the code, like this:

```js
let n = 3;
console.log([1, 2, 3].map(n = + 1)); 
``` 

```json
{
    "presets": ["es2015", { "loose": true }]
}
``` 
![babel-cli run-error](https://cloud.githubusercontent.com/assets/18028768/19697718/18f34ab6-9b1f-11e6-937f-980ccfeeae72.png)



![babel-cli run ok](https://cloud.githubusercontent.com/assets/18028768/19698847/78734e9c-9b23-11e6-9729-3c506cc4787a.png)

**Thanks for your time!**  
Anyway, now it works!  
[npm : babel-preset-es2015 ](https://www.npmjs.com/package/babel-preset-es2015)    

```sh
$ babel index.js --presets es2015 
``` 
