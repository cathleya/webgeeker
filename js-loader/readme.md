# how-to-include-a-javascript-file-in-another-javascript-file
[how-to-include-a-javascript-file-in-another-javascript-file](http://stackoverflow.com/questions/950087/how-to-include-a-javascript-file-in-another-javascript-file?page=2&tab=oldest#tab-top)

## [A JAVASCRIPT MODULE LOADER: REQUIREJS IN NODE](http://requirejs.org/docs/node.html#3)  

## [ES6 import](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import)

## 20. CMD 安装 npm install --save-dev gulp-uglify 
## new: CMD 安装 npm install --save-dev require 
```sh
	$ npm install --save-dev gulp-uglify
	$ npm install --save-dev require 
``` 
### [how-to-include-a-javascript-file-in-another-javascript-file](http://stackoverflow.com/questions/950087/how-to-include-a-javascript-file-in-another-javascript-file/39854041#39854041)

### [REQUIREJS IN NODE](http://requirejs.org/docs/node.html#3)  
sub.js (module.exports)
```js
module.exports = {
  log: function(string) {
    if(console) console.log(string);
  }
  mylog: function(){
    console.log('just for log test!');
  }
}
``` 
main.js (Usage)
```sh
var mylog =require('./sub');

mylog.log('Hurray, it works! :)');
mylog.mylog();
``` 
