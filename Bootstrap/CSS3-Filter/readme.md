# CSS3 Filter && SVG Filter

[CSS3 filter Property](http://www.w3schools.com/cssref/css3_pr_filter.asp)  

[CSS Animatable](http://www.w3schools.com/cssref/css_animatable.asp)  

[Hide an Element - display:none or visibility:hidden?](http://www.w3schools.com/css/css_display_visibility.asp)

> Definition and Usage

Some CSS properties are animatable, meaning that they can be used in animations and transitions.

Animatable properties can change gradually from one value to another, like size, numbers, percentage and color.


http://www.w3schools.com/cssref/tryit.asp?filename=trycss_anim_z-index


grayscale灰度
sepia褐色（求专业指点翻译）
saturate饱和度
hue-rotate色相旋转
invert反色
opacity透明度
brightness亮度
contrast对比度
blur模糊
drop-shadow阴影

## filter:

blur(5px)
brightness(200%)
contrast(200%)
drop-shadow(8px 8px 10px red)
grayscale(100%)
hue-rotate(90deg)
invert(100%)
opacity(30%)
saturate(8)
sepia(100%)
contrast(200%) brightness(150%)
none

## Definition and Usage

> The filter property defines visual effects (like blur and saturation) to an element (often <img>).

Default value:  none
Inherited:  no
Animatable: yes. Read about animatable
Version:    CSS3
JavaScript syntax:  object.style.WebkitFilter="grayscale(100%)"


## CSS Syntax  

filter: none | blur() | brightness() | contrast() | drop-shadow() | grayscale() | hue-rotate() | invert() | opacity() | saturate() | sepia() | url();

> Tip: To use multiple filters, separate each filter with a space (See "More Examples" below).

## Filter Functions  

Note: The filters that use percentage values (i.e. 75%), also accept the value as decimal (i.e. 0.75).


## Filter  Description 

none    Default value. Specifies no effects 

blur(px)    Applies a blur effect to the image. A larger value will create more blur. 

If no value is specified, 0 is used.    

brightness(%)   Adjusts the brightness of the image. 

0% will make the image completely black.
100% (1) is default and represents the original image.
Values over 100% will provide brighter results. 

contrast(%) Adjusts the contrast of the image.

0% will make the image completely black.
100% (1) is default and represents the original image.
Values over 100% will provide results with less contrast.   

drop-shadow(h-shadow v-shadow blur spread color)    Applies a drop shadow effect to the image. 

Possible values:
h-shadow - Required. Specifies a pixel value for the horizontal shadow. Negative values place the shadow to the left of the image.

v-shadow - Required. Specifies a pixel value for the vertical shadow. Negative values place the shadow above the image.

blur - Optional. This is the third value, and must be in pixels. Adds a blur effect to the shadow. A larger value will create more blur (the shadow becomes bigger and lighter). Negative values are not allowed. If no value is specified, 0 is used (the shadow's edge is sharp).

spread - Optional. This is the fourth value, and must be in pixels. Positive values will cause the shadow to expand and grow bigger, and negative values will cause the shadow to shrink. If not specified, it will be 0 (the shadow will be the same size as the element). 
Note: Chrome, Safari and Opera, and maybe other browsers, do not support this 4th length; it will not render if added.

color - Optional. Adds a color to the shadow. If not specified, the color depends on the browser (often black).

An example of creating a red shadow, which is 8px big both horizontally and vertically, with a blur effect of 10px:

filter: drop-shadow(8px 8px 10px red);

Tip: This filter is similar to the box-shadow property. 

grayscale(%)    Converts the image to grayscale. 

0% (0) is default and represents the original image.
100% will make the image completely gray (used for black and white images).

Note: Negative values are not allowed.  

hue-rotate(deg) Applies a hue rotation on the image. The value defines the number of degrees around the color circle the image samples will be adjusted. 0deg is default, and represents the original image.

Note: Maximum value is 360deg.  

invert(%)   Inverts the samples in the image. 

0% (0) is default and represents the original image.
100% will make the image completely inverted.

Note: Negative values are not allowed.  

opacity(%)  Sets the opacity level for the image. The opacity-level describes the transparency-level, where:

0% is completely transparent.
100% (1) is default and represents the original image (no transparency).

Note: Negative values are not allowed.
Tip: This filter is similar to the opacity property.    

saturate(%) Saturates the image. 

0% (0) will make the image completely un-saturated.
100% is default and represents the original image.
Values over 100% provides super-saturated results. 

Note: Negative values are not allowed.  

sepia(%)    Converts the image to sepia. 

0% (0) is default and represents the original image. 
100% will make the image completely sepia.

Note: Negative values are not allowed.  

url()   The url() function takes the location of an XML file that specifies an SVG filter, and may include an anchor to a specific filter element. Example:

filter: url(svg-url#element-id) 
initial Sets this property to its default value. Read about initial 
inherit Inherits this property from its parent element. Read about inherit






https://github.com/twbs/bootstrap/issues/6241

http://stackoverflow.com/questions/133051/what-is-the-difference-between-visibilityhidden-and-displaynone

http://www.cssnewbie.com/css-visibility-hidden-vs-display-none/

http://www.w3schools.com/css/css_display_visibility.asp

## Bootstrap ???

```css
.hidden {
  display: none;
  visibility: hidden;
} 

.hide {
  display: none;
}

``` 

https://blackrockdigital.github.io/startbootstrap-freelancer/

z-index: 2;