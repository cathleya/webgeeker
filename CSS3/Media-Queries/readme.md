# Media Queries
W3C Recommendation 19 June 2012

## 媒体查询由媒体类型和零个或多个表达式,检查特定媒体功能的条件。

> [Media Queries](https://www.w3.org/TR/css3-mediaqueries/)

## 媒体查询是一个逻辑表达式,要么是true要么是false。

> 不区分大小写。(case-insensitive.)

```code
# 在CSS样式表里面，我们可以声明这部分适用于某些媒体类型：

@media screen {
    * { font-family: sans-serif }
}

@media all and (min-width:500px) {
    * { font-family: sans-serif }
}

@media screen and (color), projection and (min-width:500px) {
    * { font-family: sans-serif }
}

# CSS2.1目前支持不同的媒体类型量身定制的媒体相关的样式表
> 在HTML5，这可以写为：

<link rel="stylesheet" media="screen" href="sans-serif.css">
<link rel="stylesheet" media="all and (min-width:500px)" href="serif.css">
<link rel="stylesheet" media="screen and (color), projection and (min-width:500px)" href="serif.css">


> 在HTML4，这可以写为：

<link rel="stylesheet" type="text/css" media="screen" href="sans-serif.css">
<link rel="stylesheet" type="text/css" media="all and (min-width:500px)" href="serif.css">
<link rel="stylesheet" type="text/css" media="screen and (color), projection and (min-width:500px)" href="serif.css">

> 在XHTML，这可以写为：

<link rel="stylesheet" type="text/css" media="screen" href="sans-serif.css" />
<link rel="stylesheet" type="text/css" media="all and (min-width:500px)" href="serif.css" />
<link rel="stylesheet" type="text/css" media="screen and (color), projection and (min-width:500px)" href="serif.css" />

# 在XML，这可以写为：

<?xml-stylesheet media="screen and (color), projection and (color)" rel="stylesheet" href="example.css" ?>

# 用 import (no need media)，这可以写为：

@import url(example.css) screen and (color), projection and (color);


```

## media types ?
The ‘print’ and ‘screen’ media types are defined in HTML4.  
打印”和“屏幕”媒体类型在HTML4定义。

 The complete list of media types in HTML4 is: ‘aural’, ‘braille’, ‘handheld’, ‘print’, ‘projection’, ‘screen’, ‘tty’, ‘tv’.  
 在HTML4媒体类型的完整列表是：“听觉”，“点字/盲文”，“手持式”，“打印”，“投影”，“屏幕”，“TTY”，“电视”.

 CSS2 defines the same list, deprecates ‘aural’ and adds ‘embossed’ and ‘speech’. Also, ‘all’ is used to indicate that the style sheet applies to all media types.  
 CSS2定义了相同的列表中，弃用“听觉”，并增加了“浮雕/压花”和“讲话/语音”。  
 此外，“全部”被用来指示该样式表适用于所有介质类型。   

 ‘speech’ ? 屏幕阅读器 : 讲话/语音

## 下面是识别的媒体描述符的列表

* screen  
  用于非分页的计算机屏幕。    
  Intended for non-paged computer screens.  
* tty   
  适用于使用固定宽字符网格的媒介，如电传打字机，终端，或具有有限显示能力的便携式设备。  
  Intended for media using a fixed-pitch character grid, such as teletypes, terminals, or portable devices with limited display capabilities.
* tv  
  用于电视类设备（分辨率低，色彩，有限的可滚动）。  
  Intended for television-type devices (low resolution, color, limited scrollability).  
* projection(投影)  
  针对投影机。(Intended for projectors.)  
* handheld   
  用于手持设备（小屏幕，单色,位图图形，有限的带宽）。  
  Intended for handheld devices (small screen, monochrome, bitmapped graphics, limited bandwidth).  
* print  
  针对分页，不透明材料以及在打印预览模式下在屏幕上查看的文档。  
  Intended for paged, opaque material and for documents viewed on screen in print preview mode.  
* braille(点字/盲文)  
  Intended for braille tactile feedback devices.  
* aural(听觉)  
  用于语音合成器。(Intended for speech synthesizers.)  
* all  
  适用于所有设备。(Suitable for all devices.)  

> screen , all , all and ===  


```code
# screen

<link rel="stylesheet" media="screen and (color)" href="example.css" />

@import url(color.css) screen and (color);

```

## media feature (?)

### max/min (prefix) optional

> Media features

4.1. width  
4.2. height  
4.3. device-width  
4.4. device-height  
4.5. orientation  
4.6. aspect-ratio   (纵横比: 16/9)  
4.7. device-aspect-ratio  (设备纵横比)  
4.8. color  
4.9. color-index  (颜色索引)   
4.10. monochrome (	单色, 黑白的)  
4.11. resolution  (解析度)  
4.12. scan  
4.13. grid  

```code
# (color)

<link rel="stylesheet" media="screen and (color)" href="example.css" />

@import url(color.css) screen and (color);

```



## media query list

> 逗号分隔的列表(comma-separated list)

@media screen and (color), projection and (color) { … }

> 以逗号分隔的媒体查询列表。如果一个或多个在逗号分隔列表中的媒体查询为真，整个名单是真实的，否则为false。











## keyword ‘all’

一个简写语法可供适用于所有媒体类型媒体查询;
关键字'all'可以（与尾随“and”一起）省略。
如果媒体类型是没有明确给出这是“所有”。

```code
I.e. 这些是相同的：

@media (min-width:500px) { … }
@media all and (min-width:500px) { … }

#如同是这些：

@media (orientation: portrait) { … }
@media all and (orientation: portrait) { … }
```

## Usage of ?

```code
# Here is the same example written in HTML, XHTML, XML, @import and @media:

<link rel="stylesheet" media="screen and (color), projection and (color)" rel="stylesheet" href="example.css">

<link rel="stylesheet" media="screen and (color), projection and (color)" rel="stylesheet" href="example.css" />

<?xml-stylesheet media="screen and (color), projection and (color)" rel="stylesheet" href="example.css" ?>

@import url(example.css) screen and (color), projection and (color);

@media screen and (color), projection and (color) { … }

```

## keyword ‘only’

```code
<link rel="stylesheet" media="only screen and (color)" href="example.css" />
```

## keyword ‘not’

```code
<link rel="stylesheet" media="not screen and (color)" href="example.css" />
```

* [more coming soon ...](http://xgqfrms.xyz)
