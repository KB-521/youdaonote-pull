使用场景：大型数据运算、计时器、异步请求、访问navigator部分属性、js核心对象；



使用Worker：

```javascript
//主进程文件
var worker = new Worker('worker.js'); //定义子进程文件
worker.postMessage(data); //传入数据
worker.onmessage = function(e){} //取出完成的数据
//worker文件
onmussage = function(e){
    e.data; //接收的传入的数据
    postMessage(); //传出数据
}
```

结束Worker：

```javascript
close(); //在worker子进程文件中使用
worker.terminate(); //在主进程文件中使用
```



局限性：

1. 不能跨域加载 (必需在服务器下，本地文件不能使用)；

1. worker文件不能访问DOM；