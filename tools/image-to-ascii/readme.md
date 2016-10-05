#  image-to-ascii

[https://github.com/ufo-github/image-to-ascii](https://github.com/ufo-github/image-to-ascii)

[https://github.com/IonicaBizau/github-contributions](https://github.com/IonicaBizau/github-contributions) 



### 配置环境，安装必要的插件
image-to-ascii 依赖于 Graphics Magick，所以我们先安装Graphics Magick

```sh
#  Ubuntu
$ sudo apt-get install graphicsmagick

#  Fedora
$ sudo dnf install GraphicsMagick

#  OS X
$ brew install graphicsmagick

#  Chocolatey (package manager for Windows)
#  (Restart of cmd/PowerShell is required)
$ choco install graphicsmagick
``` 

> 我的安装环境是mac，但是在Graphics Magick的安装过程中出现了一些错误，  
后来我使用的是port才把这个graphicsmagick安装成功 

```sh
port install graphicsmagick
``` 

>安装graphicsmagick成功后，我们新建一个项目文件夹，名叫“imageToAscii”，再文件夹下终端使用npn创建一个项目  

```sh
$ npm init
``` 

>依次按提示输入项目的名称，版本，开源协议等等信息。  

接着我们安装ImageToAscii  

```sh
$ npm install image-to-ascii --save-dev
``` 

>安装完成之后项目文件夹会多一个node_modules，里面存放相关依赖的node包 

编写nodejs代码 

项目根目录下创建一个文件，index.js，代码如下： 


```js

//导入image-to-ascii 包
var ImageToAscii = require("image-to-ascii");
//配置一个图片的根路径
var __dirname = "./images/";

//调用image-to-ascii的方法，2个参数，第一个为图片的路径，第二个为完成后的输出。

ImageToAscii(__dirname + '2.jpg',function(err,converted){
	console.log(err || converted)
});
``` 

>代码很简单，注意看我的注释。  

调用nodejs，把图片打印成ascii  

代码写完之后，我们打开终端，进入到项目的根目录，执行我们写的index.js代码  

```sh
$ node index.js
``` 








