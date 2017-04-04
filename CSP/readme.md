# CSP

https://developers.google.com/web/fundamentals/security/csp/

CSP 基于白名单来源，因为此方法可明确指示浏览器将特定的资源集视为可接受的资源，并拒绝其余资源。


```html
<meta http-equiv="Content-Security-Policy" 
content="default-src https://cdn.example.net; child-src 'none'; object-src 'none'" />
```

内联代码被视为是有害的。

很明显，CSP 基于白名单来源，因为此方法可明确指示浏览器将特定的资源集视为可接受的资源，并拒绝其余资源。不过，基于来源的白名单无法解决 XSS 攻击带来的最大威胁：内联脚本注入。如果攻击者可以注入一个 script 标记，在标记中直接包含一些恶意的负载 (`<script>sendMyDataToEvilDotCom();</script>`)，则浏览器将无法将它与合法内联脚本标记区分开来。CSP 可通过完全禁止内联脚本来解决此问题：这是唯一确定有效的方式。

此禁止规则不仅包括在 script 标记中直接嵌入的脚本，也包括内联事件处理程序和 javascript: 网址。 您需要将 script 标记的内容移入外部文件，并使用相应的 addEventListener() 调用替换 javascript: 网址和 `<a ... onclick="[JAVASCRIPT]">`。 例如，您可以将以下内容

```js
<script>
  function doAmazingThings() {
    alert('YOU AM AMAZING!');
  }
</script>
<button onclick='doAmazingThings();'>Am I amazing?</button>

// 重写为下面这样：


<!-- amazing.html -->
<script src='amazing.js'></script>
<button id='amazing'>Am I amazing?</button>
// amazing.js
function doAmazingThings() {
  alert('YOU AM AMAZING!');
}
document.addEventListener('DOMContentReady', function () {
  document.getElementById('amazing')
    .addEventListener('click', doAmazingThings);
});

```

除了能够更好地配合 CSP 外，重写的代码还具有许多优势；无论您是否使用 CSP，这都是最佳做法。 内联 JavaScript 混合结构和行为的方式正是您不应采用的方式。使用外部资源，浏览器更容易缓存，开发者也更容易理解，并有助于编译和压缩。如果您将代码移入外部资源，那么您可以编写更好的代码。

以相同方式处理内联样式：style 属性和 style 标记都应合并到外部样式表，以防范可通过 CSS 实现的各种[极其狡猾的](https://scarybeastsecurity.blogspot.jp/2009/12/generic-cross-browser-cross-domain.html)数据渗漏方法。



## Generic cross-browser cross-domain theft 通用跨浏览器跨域盗用

https://scarybeastsecurity.blogspot.jp/2009/12/generic-cross-browser-cross-domain.html

Well, here's a nice little gem for the festive season. I like it for a few distinct reasons:

It's one of those cases where if you look at web standards from the correct angle, you can see a security vulnerability specified.

Accordingly, it affected all 5 major browsers. And likely the rest.

You can still be a theft victim even with plugins and JavaScript disabled!

即使插件和JavaScript禁用，你仍然可以成为偷盗的受害者！



```js

https://www.google.com/%3C/a%3E%3Cbr/%3E%3Cspan%20class=%22j%22%3EChris%20Evans%3C/span%3E%3C/span%3E%3C/div%3E%3C/div%3E%3Cdiv%20class=%22h%22%3E%3Cdiv%20class=%22i%22%3E%3Cspan%3E%3Ca%20href=%22/p/mail/messageDetail?fid=Inbox&amp;mid=1_3493_AGvHtEQAAWFgSgIzgAlWYQXHqDY&3=q%22%3ESuper%20sensitive%20subject%3C/a%3E%3Cbr/%3E%3Cspan%20class=%22j%22%3EChris%20Evans%3C/span%3E%3C/span%3E%3C/div%3E%3C/div%3E%3Cdiv%20class=%22h%22%3E%3Cdiv%20class=%22i%22%3E%3Cspan%3E%3Ca%20href=%22/p/mail/messageDetail?fid=Inbox&amp;mid=1_3933_AGTHtEQAAM%2FHSgIzawpE8Fwm1%2FI&5=x%22%3E


```

https://scarybeastsecurity.blogspot.jp/

## Ubuntu 16.04 LTS exploit
https://www.youtube.com/watch?v=wrCLoem6ggM






