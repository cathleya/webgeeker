# CSP

https://developers.google.com/web/fundamentals/security/csp/

CSP 基于白名单来源，因为此方法可明确指示浏览器将特定的资源集视为可接受的资源，并拒绝其余资源。


```html
<meta http-equiv="Content-Security-Policy" 
content="default-src https://cdn.example.net; child-src 'none'; object-src 'none'" />
```












