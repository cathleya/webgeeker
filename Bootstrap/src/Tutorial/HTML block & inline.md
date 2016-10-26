# The Difference Between HTML Block and Inline Elements

> block-level elements and inline elements.

> 块级元素和内联元素。


## HTML Block Elements

1. 独占一行  
2. 可以设置width,height  

> 具有，但可以不限于，下列特征  

如果没有宽度设置，自然会扩大，以填补其父容器;  
可以有margins 和/或 padding;  
如果没有高度设置，自然会扩大，以适应其子元素（假设他们不浮动或定位）;  
默认情况下，将放在前面的元素在下面的标记（假设周围的元素没有浮动或定位）;  
忽略vertical-align属性;  

```html
<p>, <div>, <form>, <header>, <nav>, <ul>, <li>, and <h1>.
``` 


## HTML Inline Elements

1. 仅仅占内容宽度  
2. 不可以设置width,height属性  
(除非使用：display：block/inline block)  

> 具有，但可以不限于，下列特征  

文字内容一起流动，从而;  
不会清除以前的内容将下降到像块级元素的下一行;  
受CSS中的空白设置的控制;  
将忽略上,下margin设置，但将适用于左,右margin，任何padding;  
会忽略width和height属性;  
如果浮动左或右，将自动成为一个块级元素，受到了块特性;  
受vertical-align属性控制;  

```html
<a>, <span>, <b>, <em>, <i>, <cite>, <mark>, and <code>.  
``` 






## block inline block

block === block 

??? 

inline block ===  inline + width,height


## box-sizing: border-box/content-box;




> links:

[The Difference Between “Block” and “Inline”](https://www.impressivewebs.com/difference-block-inline-css/)

* By Louis Lazaris on November 30th, 2011

> 该块的例子是结构元素，而行内元素是基于文本的。

> 有一个例外：你可以用一个<a>元素包裹的任何内容，无论是块级元素，内联元素，或两者的混合。

替换元素:  
<img>, <object>, <input>, and <select>.

[]()

*

[]()

*

[HTML 4 Block-Level Elements](http://htmlhelp.com/reference/html40/block.html)

[HTML 4 Inline Elements](http://htmlhelp.com/reference/html40/inline.html)


*

[Block-level elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Block-level_elements)

[Inline elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Inline_elements)


[understand-inline-and-block-level-elements](http://blog.digitaltutors.com/understand-inline-and-block-level-elements/)

[replacedelements](http://reference.sitepoint.com/css/replacedelements)

A replaced element is any element whose appearance and dimensions are defined by an external resource. Examples include images (<img> tags), plugins (<object> tags), and form elements (<button>, <textarea>, <input>, and <select> tags). All other elements types can be referred to as non-replaced elements.

[Layout Properties](https://www.sitepoint.com/web-foundations/layout/)

















