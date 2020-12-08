---
title: HTTP、TCP、UDP、Socket、HTTPS区别
date: 2018-10-11 11:28:29
tags:
    - http
    - tcp
    - udp
    - socket
categories: http
---
<center>![](was-ist-http-t.jpg)</center>

### 简介
* `TCP/IP`是个协议组，可分为四个层次：网络接口层、网络层、传输层和应用层，如下图所示
<center>![](20170328194734804.png)</center>
* 在网络层有`IP协议`、`ICMP协议`、`ARP协议`、`RARP协议`和`BOOTP协议`。
* 在传输层中有`TCP协议`与`UDP协议`。
* 在应用层有`HTTP`,`FTP`、`TELNET`、`SMTP`、`DNS`等协议。

### 详细介绍
#### HTTP(HyperText Transfer Protocal)
`HTTP`(`HyperText Transfer Protocal`),超文本传输协议，HTTP连接最显著的特点是客户端发送的每次请求都需要服务器回送响应，在请求结束后，会主动释放连接。从建立连接到关闭连接的过程称为"一次连接"。

##### 优点
* 基于应用级的接口使用方便
* 程序员开发水平要求不高，容错性强

##### 缺点
* 传输速度慢，数据包大（`Http协议中包含辅助应用信息`）
* 如实时交互，服务器性能压力大。
* 数据传输安全性差

##### 适用范围
基于http协议传输方式适合于对传输速度，安全性要求不是很高，且需要快速开发的应用。如公司OA系统，互联网服务等。

#### HTTPS
`HTTPS`(`Secure Hypertext Transfer Protocol`),安全超文本传输协议，它是一个安全通信通道。`HTTPS`是`HTTP over SSL/TLS`，`HTTP`是应用层协议，`TCP`是传输层协议，在应用层和传输层之间，增加了一个安全套接层`SSL/TLS`：
> * `SSL` (`Secure Socket Layer`，安全套接字层)
* `TLS` (`Transport Layer Security`，传输层安全协议)
* `SSL`使用`40`位关键字作为`RC4`流加密算法

#### Https和Http区别
* https协议需要到`CA`申请证书。
* http是超文本传输协议，信息是明文传输；https 则是具有安全性的ssl加密传输协议。
* http和https使用的是完全不同的连接方式，用的端口也不一样，前者是`80`，后者是`443`。
* http的连接很简单，是无状态的；HTTPS协议是由`SSL+HTTP`协议构建的可进行加密传输、身份认证的网络协议，比http协议安全。

#### TCP
传送控制协议(`Transmission Control Protocol`)
#### UDP
用户数据报协议 （`UDP：User Datagram Protocol`） 
#### socket
这是为了实现以上的通信过程而建立成来的通信管道，其真实的代表是客户端和服务器端的一个通信进程，双方进程通过socket进行通信，而通信的规则采用指定的协议。`socket只是一种连接模式，不是协议`，socket是对TCP/IP协议的封装，Socket本身并不是协议，而是一个`调用接口（API）`，通过Socket，我们才能使用TCP/IP协议。tcp、udp，简单的说（虽然不准确）是两个最基本的协议,很多其它协议都是基于这两个协议如，http就是基于tcp的，用socket可以创建tcp连接，也可以创建udp连接，这意味着，用socket可以创建任何协议的连接，因为其它协议都是基于此的。
##### 优点
 * 传输数据为字节级，传输数据可自定义，数据量小（对于手机应用讲：费用低）
 * 传输数据时间短，性能高
 * 适合于客户端和服务器端之间信息实时交互
 * 可以加密,数据安全性强

##### 缺点
* 需对传输的数据进行解析，转化成应用级的数据
* 对开发人员的开发水平要求高
* 相对于Http协议传输，增加了开发量

##### 适用范围
Socket传输方式适合于对传输速度，安全性，实时交互，费用等要求高的应用中，如网络游戏，手机应用，银行内部交互等

**参考资料**
* [HTTP、TCP、UDP，Socket，HTTPS](https://blog.csdn.net/WHB20081815/article/details/67640804)
