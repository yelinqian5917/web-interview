# 跨域

## 什么是跨域？

跨域，是指浏览器不能执行其他网站的脚本。它是由浏览器的同源策略造成的，是浏览器对JavaScript实施的安全限制。

## 跨域的情况

- 协议
- 域名
- 端口
三者有一个不同则为跨域

## 跨域解决方法

### 1. 通过jsonp跨域
通常为了减轻web服务器的负载，我们把js、css，img等静态资源分离到另一台独立域名的服务器上，在html页面中再通过相应的标签从不同域名下加载静态资源，而被浏览器允许，基于此原理，我们可以通过动态创建script，再请求一个带参网址实现跨域通信。
jsonp缺点：只能实现get一种请求。

### 2. document.domain + iframe跨域

### 3. location.hash + iframe

### 4. window.name + iframe跨域

### 5. postMessage跨域

消息传递
window.postMessage() 方法允许来自一个文档的脚本可以传递文本消息到另一个文档里的脚本，而不用管是否跨域，可以用这种消息传递技术来实现安全的通信。这项技术称为“跨文档消息传递”，又称为“窗口间消息传递”或者“跨域消息传递”。

#### postMessage 可用于解决以下方面的问题：
页面和其打开的新窗口的数据传递
页面与嵌套的 iframe 消息传递
多窗口之间消息传递
上面三个问题的跨域数据传递

- 发送消息
```js
otherWindow.postMessage(message, targetOrigin, [transfer]);
```

**otherWindow**
其他窗口的一个引用。比如 iframe 的 contentWindow 属性、执行 window.open 返回的窗口对象、或者是命名过或数值索引的 window.frames。

**message**
要发送的消息。它将会被结构化克隆算法序列化，所以无需自己序列化，html5规范中提到该参数可以是JavaScript的任意基本类型或可复制的对象，然而并不是所有浏览器都做到了这点儿，部分浏览器只能处理字符串参数，所以我们在传递参数的时候需要使用JSON.stringify()方法对对象参数序列化。

**targetOrigin**
“目标域“。URI（包括：协议、主机地址、端口号）。若指定为”*“，则表示可以传递给任意窗口，指定为”/“，则表示和当前窗口的同源窗口。当为URI时，如果目标窗口的协议、主机地址或端口号这三者的任意一项不匹配 targetOrigin 提供的值，那么消息就不会发送。

- 接收消息
```js
window.addEventListener('message',function(e) {
   var origin = event.origin;
   // 通常，onmessage()事件处理程序应当首先检测其中的origin属性，忽略来自未知源的消息
   if (origin !== "http://example.org:8080") return;
   // ...
}, false)
```

#### 示例

```js
/**
* localhost:10002/index页面
**/
// 接收消息
window.addEventListener('message', (e) => {
     console.log(e.data)
})
// 发送消息
const targetWindow = window.open('http://localhost:10001/user');
setTimeout(() => {
     targetWindow.postMessage('来自10002的消息', 'http://localhost:10001')
}, 3000)

```

```js
/**
* localhost:10001/user页面
**/
window.addEventListener('message', (e) => {
     console.log(e.data)
     if (event.origin !== "http://localhost:10002") return;
     e.source.postMessage('来自10001的消息', e.origin)
})

```

### 6. 跨域资源共享（CORS）

### 7. nginx代理跨域

### 8. nodejs中间件代理跨域

### 9. WebSocket协议跨域