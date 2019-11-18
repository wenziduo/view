### 浏览器缓存的请求头

强缓存
Expires
Cache-Control

协商缓存
Etag If-Not-Match
Last-Modified If-Modified-Since
浏览器会根据 http response header 中的 Expires 和 cahe-control 字段判断是否命中强缓存，如若命中，则直接从缓存中取资源，不会再去向服务器请求了。否则（没有命中强缓存），浏览器会发出一个条件请求，浏览器会在请求头中包含 If-Modified-Since 或 If-None-Match 字段，If-Modified-Since 即浏览器当初得到的 Last-Modified；If-None-Match 即浏览器当初得到的 ETag。当服务器发现资源的更新时间晚于 If-Modified-Since 所提供的时间，或者资源在服务器端当前的 ETag 和 If-None-Match 提供的不符时，说明该资源需要向服务器重新请求了。否则，浏览器将不需要重新下载整个资源，只需要从缓存中去加载这个资源，这时响应的 http code 为 304（304 Not Modified）。
等强缓存阶段的时候检测了下，发现缓存已经过期了。就需要去找原始服务器取对应的数据，原始服务器检查下自己的数据有没有更新过，一样就说用之前的就行，如果更新了，就请求，200.没有更新，就304

### http 和 https 的区别
HTTP加上加密处理和认证以及完整性保护后即是https。

1、https 协议需要到 ca 申请证书，一般免费证书较少，因而需要一定费用。

2、http 是超文本传输协议，信息是明文传输，https 则是具有安全性的 ssl 加密传输协议。

3、http 和 https 使用的是完全不同的连接方式，用的端口也不一样，前者是 80，后者是 443。

4、http 的连接很简单，是无状态的；HTTPS 协议是由 SSL+HTTP 协议构建的可进行加密传输、身份认证的网络协议，比 http 协议安全。
### 跨域得三要素
同源/同端口/协议
### localStorage/cookie/sessionStorage
容量/时间/与服务端交互
