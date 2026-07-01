# 计算机网络学习笔记

<span class="important-note">本笔记系统讲解计算机网络的核心概念，从物理层到应用层，帮助您建立完整的网络知识体系。</span>

## OSI七层模型

### 第一层：物理层

负责传输比特流，使用电缆、光纤等物理介质。

### 第二层：数据链路层

负责帧的传输，包含MAC地址。

<span class="tip-box">常见设备：交换机、网桥</span>

### 第三层：网络层

负责数据包的路由，使用IP地址。

### 第四层：传输层

负责端到端的通信，包含TCP和UDP协议。

<span class="warning-box">TCP面向连接、可靠传输；UDP无连接、不可靠但效率高。</span>

### 第五层：会话层

管理应用程序之间的通信会话。

### 第六层：表示层

负责数据的加密、解密和压缩。

### 第七层：应用层

提供应用程序接口，如HTTP、FTP、DNS等。

## TCP三次握手

```
客户端          服务器
  |               |
  |---- SYN ----->|
  |               |
  |<--- SYN+ACK --|
  |               |
  |---- ACK ----->|
  |               |
  |==== 连接建立 ====|
```

<span class="tip-box">三次握手的目的：防止已失效的连接请求突然又传送到了服务端。</span>

## HTTP状态码

- 200：成功
- 301：永久重定向
- 404：未找到
- 500：服务器错误

```javascript
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log(data));
```

> 网络是计算机之间通信的桥梁，理解网络原理对于开发至关重要。