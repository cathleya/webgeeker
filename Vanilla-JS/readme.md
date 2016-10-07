#  Vanilla JS 

> Vanilla JS is a fast, lightweight, cross-platform framework for building incredible, powerful JavaScript applications.

[http://vanilla-js.com/](http://vanilla-js.com/)  

![logo](http://vanilla-js.com/assets/button.png)


## Getting Started
The Vanilla JS team takes pride in the fact that it is the most lightweight framework available anywhere; 
using our production-quality deployment strategy,  
your users' browsers will have Vanilla JS loaded into memory before it even requests your site.

To use Vanilla JS, just put the following code anywhere in your application's HTML:

```code
<script src="path/to/vanilla.js"></script>
``` 

When you're ready to move your application to a production deployment, switch to the much faster method:

 
> # That's right - no code at all.  (你没看错！没有任何代码，Vanilla JS 太流行了，所有的浏览器在十年前就已经内置了它。) 
> Vanilla JS is so popular that browsers have been automatically loading it for over a decade.

## Speed Comparison 
Here are a few examples of just how fast Vanilla JS really is:

> Retrieve DOM element by ID  
* Code	ops / sec 
Vanilla JS	document.getElementById('test-table');	
12,137,211
 
Dojo	dojo.byId('test-table');	
5,443,343
 
Prototype JS	$('test-table')	
2,940,734
 
Ext JS	delete Ext.elCache['test-table']; Ext.get('test-table');	
997,562
 
jQuery	$jq('#test-table');	
350,557
 
YUI	YAHOO.util.Dom.get('test-table');	
326,534
 
MooTools	document.id('test-table');	
78,802
 
## Retrieve DOM elements by tag name 
* Code	ops / sec 
Vanilla JS	document.getElementsByTagName("span");	
8,280,893
 
Prototype JS	Prototype.Selector.select('span', document);	
62,872
 
YUI	YAHOO.util.Dom.getElementsBy(function(){return true;},'span');	
48,545
 
Ext JS	Ext.query('span');	
46,915
 
jQuery	$jq('span');	
19,449
 
Dojo	dojo.query('span');	
10,335
 
MooTools	Slick.search(document, 'span', new Elements);	
5,457
 
# Code Examples 
* Here are some examples of common tasks in Vanilla JS and other frameworks:

> Fade an element out and then remove it 

## Vanilla JS	
```js
var s = document.getElementById('thing').style;
s.opacity = 1;
(function fade(){(s.opacity-=.1)<0?s.display="none":setTimeout(fade,40)})();
``` 

## jQuery	
```js
<script src="//ajax.googleapis.com/ajax/libs/jquery/1/jquery.min.js"></script>
<script>
$('#thing').fadeOut();
</script>
``` 

> Make an AJAX call

## Vanilla JS	
```js
var r = new XMLHttpRequest();
r.open("POST", "path/to/api", true);
r.onreadystatechange = function () {
  if (r.readyState != 4 || r.status != 200) return;
  alert("Success: " + r.responseText);
};
r.send("banana=yellow");
```

## jQuery	
```js
<script src="//ajax.googleapis.com/ajax/libs/jquery/1/jquery.min.js"></script>
<script>
$.ajax({
  type: 'POST',
  url: "path/to/api",
  data: "banana=yellow",
  success: function (data) {
    alert("Success: " + data);
  },
});
</script>
``` 

Further Reading
For more information about Vanilla JS:

check out the Vanilla JS documentation
read some books on Vanilla JS
or try out one of the many Vanilla JS plugins.
When powering your applications with Vanilla JS, feel free to use this handy button!

























