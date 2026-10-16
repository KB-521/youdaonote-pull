Web Socket优点：

1. 客户端与服务器都可以主动传数据给对方；

1. 不同频繁创建TCP请求及销毁请求，减少网络带宽的占用，也可以节省服务器资源



Web Socket使用了自定义协议，url方案有变化，所以不能再使用http、https协议，而是要使用ws://、wss://。前者不是安全连接，后者是安全连接。



创建Web Socket：

```javascript
var Socket = new WebSocket('请求的地址'); 
```

方法：

```javascript
Socket.send(data); // 传输数据,必需在连接成功后使用
Socket.close(); // 终止连接
```

事件：

```javascript
Socket.onopen = () => {}; // 连接成功后触发
Socket.onmessage = () => {}; // 指定从服务器接受到信息时触发
Socket.onerror = () => {}; // 连接失败后触发
Socket.onclose = () => {}; // 连接关闭后触发
```

