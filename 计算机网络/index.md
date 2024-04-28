# 计算机网络

## 从浏览器地址栏输入url到显示主页的过程
1. DNS解析，查找域名对应的IP地址。
2. 与服务器通过三次握手，建立TCP连接
3. 向服务器发送HTTP请求
4. 服务器处理请求，返回网页内容
5. 浏览器解析并渲染页面
6. TCP四次挥手，连接结束





## 11.在交互过程中如果数据传送完了，还不想断开连接怎么办，怎么维持？
这个问题记住keep-alive就好，也就是说，在HTTP中响应体的Connection字段指定为keep-alive即可

## 12.HTTP 如何实现长连接？在什么时候会超时？
这道题实际上是考察TCP长连接的知识点，HTTP的长连接实质是指TCP的长连接。至于什么时候超时，我们记住这几个参数如tcp_keepalive_time、tcp_keepalive_probes就好啦

### 12.1 什么是HTTP的长连接？
1. HTTP分为长连接和短连接，本质上说的是TCP的长短连接。TCP连接是一个双向的通道，它是可以保持一段时间不关闭的，因此TCP连接才具有真正的长连接和短连接这一说法哈。

2. TCP长连接可以复用一个TCP连接，来发起多次的HTTP请求，这样就可以减少资源消耗，比如一次请求HTML，如果是短连接的话，可能还需要请求后续的JS/CSS。

### 12.2 如何设置长连接？
通过在头部（请求和响应头）设置Connection字段指定为keep-alive，HTTP/1.0协议支持，但是是默认关闭的，从HTTP/1.1以后，连接默认都是长连接。

### 12.3 在什么时候会超时呢？
- HTTP一般会有httpd守护进程，里面可以设置keep-alive timeout，当tcp连接闲置超过这个时间就会关闭，也可以在HTTP的header里面设置超时时间
- TCP 的keep-alive包含三个参数，支持在系统内核的net.ipv4里面设置；当 TCP 连接之后，闲置了tcp_keepalive_time，则会发生侦测包，如果没有收到对方的ACK，那么会每隔 tcp_keepalive_intvl再发一次，直到发送了tcp_keepalive_probes，就会丢弃该连接。

```
tcp_keepalive_intvl = 15
tcp_keepalive_probes = 5
tcp_keepalive_time = 1800
```





## 说说DNS的解析过程？
1. 首先会查找浏览器的缓存,看看是否能找到www.baidu.com对应的IP地址，找到就直接返回；否则进行下一步。
2. 将请求发往给本地DNS服务器，如果查找到也直接返回，否则继续进行下一步；
3. 本地DNS服务器向根域名服务器发送请求，根域名服务器返回负责.com的顶级域名服务器的IP地址的列表。
4. 本地DNS服务器再向其中一个负责.com的顶级域名服务器发送一个请求，返回负责.baidu的权威域名服务器的IP地址列表。
5. 本地DNS服务器再向其中一个权威域名服务器发送一个请求，返回www.baidu.com所对应的IP地址。

##  forward和redirect的区别？
直接转发方式（Forward） ，客户端和浏览器只发出一次请求，Servlet、HTML、JSP或其它信息资源，由第二个信息资源响应该请求，在请求对象request中，保存的对象对于每个信息资源是共享的。
间接转发方式（Redirect） 实际是两次HTTP请求，服务器端在响应第一次请求的时候，让浏览器再向另外一个URL发出请求，从而达到转发的目的。

## Session和Cookie的区别。
我们先来看Session和Cookie的概念吧：

Cookie是保存在客户端的一小块文本串的数据。客户端向服务器发起请求时，服务端会向客户端发送一个Cookie，客户端就把Cookie保存起来。在客户端下次向同一服务器再发起请求时，Cookie被携带发送到服务器。服务器就是根据这个Cookie来确认身份的。
session指的就是服务器和客户端一次会话的过程。Session利用Cookie进行信息处理的，当用户首先进行了请求后，服务端就在用户浏览器上创建了一个Cookie，当这个Session结束时，其实就是意味着这个Cookie就过期了。Session对象存储着特定用户会话所需的属性及配置信息。

## TCP 和 UDP 分别对应的常见应用层协议有哪些？
基于TCP的应用层协议有：HTTP、FTP、SMTP、TELNET、SSH

HTTP：HyperText Transfer Protocol（超文本传输协议），默认端口80
FTP: File Transfer Protocol (文件传输协议), 默认端口(20用于传输数据，21用于传输控制信息)
SMTP: Simple Mail Transfer Protocol (简单邮件传输协议) ,默认端口25
TELNET: Teletype over the Network (网络电传), 默认端口23
SSH：Secure Shell（安全外壳协议），默认端口 22
基于UDP的应用层协议：DNS、TFTP、SNMP

DNS : Domain Name Service (域名服务),默认端口 53
TFTP: Trivial File Transfer Protocol (简单文件传输协议)，默认端口69
SNMP：Simple Network Management Protocol（简单网络管理协议），通过UDP端口161接收，只有Trap信息采用UDP端口162。

## URI和URL的区别
- URI，全称是Uniform Resource Identifier)，中文翻译是统一资源标志符，主要作用是唯一标识一个资源。
- URL，全称是Uniform Resource Location)，中文翻译是统一资源定位符，主要作用是提供资源的路径。打个经典比喻吧，URI像是身份证，可以唯一标识一个人，而URL更像一个住址，可以通过URL找到这个人。

## 请详细介绍一下TCP 的三次握手机制
TCp提供可靠的连接服务，连接是通过三次握手进行初始化的。三次握手的目的就是同步连接双方的序列号和确认号并交换TCP窗口大小信息。

- 第一次握手(SYN=1, seq=x)，发送完毕后，客户端就进入SYN_SEND状态
- 第二次握手(SYN=1, ACK=1, seq=y, ACKnum=x+1)， 发送完毕后，服务器端就进入SYN_RCV状态。
- 第三次握手(ACK=1，ACKnum=y+1)，发送完毕后，客户端进入ESTABLISHED状态，当服务器端接收到这个包时，也进入ESTABLISHED状态。

## 说说TCP四次挥手过程
第一次挥手(FIN=1，seq=u)，发送完毕后，客户端进入FIN_WAIT_1状态。
第二次挥手(ACK=1，ack=u+1,seq =v)，发送完毕后，服务器端进入CLOSE_WAIT状态，客户端接收到这个确认包之后，进入FIN_WAIT_2状态。
第三次挥手(FIN=1，ACK1,seq=w,ack=u+1)，发送完毕后，服务器端进入LAST_ACK状态，等待来自客户端的最后一个ACK。
第四次挥手(ACK=1，seq=u+1,ack=w+1)，客户端接收到来自服务器端的关闭请求，发送一个确认包，并进入TIME_WAIT状态，等待了某个固定时间（两个最大段生命周期，2MSL，2 Maximum Segment Lifetime）之后，没有收到服务器端的ACK ，认为服务器端已经正常关闭连接，于是自己也关闭连接，进入CLOSED状态。服务器端接收到这个确认包之后，关闭连接，进入CLOSED状态。

## 请简述TCP和UDP的区别

|              |    TCP     |     UDP      |
| :----------: | :--------: | :----------: |
| 是否面向连接 |  面向连接  |  面向无连接  |
| 是否可靠服务 |  可靠服务  | 无法保证可靠 |
|   传输速度   |   传输慢   |    传输快    |
|   报文格式   | 面向字节流 |   面向报文   |
|   使用场景   |  网页邮件  |   语音广播   |


## 链接
https://mp.weixin.qq.com/s?__biz=MzU0OTE4MzYzMw==&mid=2247517969&idx=3&sn=a0fc88111492f5529fef14008a1bb451&chksm=fbb10eefccc687f98eda6c8d7d73e251d9dc597bbece4e54d51b7607397b526c595452815e71&scene=27
