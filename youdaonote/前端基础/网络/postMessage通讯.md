方法安全的启用window对象之间的跨域通信。提供一种受控制的机制来安全的规避同源策略；



```javascript
window.frames[name]; //可以找到对应name名的iframe
window.postMessage(传输的数据,'协议+域名'); //传输
message = Fun(messageEvent){}; //该事件能接受传输来的协议 
messageEvent.data; //传输来的数据
messageEvent.origin; //传输源头的协议+域名
```

