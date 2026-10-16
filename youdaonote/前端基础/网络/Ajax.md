ajax：Asynchronous JavaScript and XML(异步的JavaScript和XML)，可实现异步、局部的获取数据；

ajax受同源策略影响；



JSON：

```javascript
var data = {"name":"king" , "age":20};//json的格式(注意双引号)
JSON.parse(data); //json格式字符串 装换为 json
JSON.stringify(data); //json 转换为 字符串
```



ajax过程：

```javascript
(1)web浏览器
(2)ajax对象
(3)初始化HTTP请求参数(请求方式，地址,同步异步)
(4)发送请求
(5)监控数据
(6)检查数据使用
```



readyState五种状态：

```javascript
xml.readyState;
// 0 -(未初始化)还没有调用send()方法
// 1 -(载入)已经调用send()方法,正在发送请求
// 2 -(载入完成)send()方法执行完成,已经接收到全部响应内容
// 3 -(交互)正在解析响应内容
// 4 -(完成)响应内容解析完成,可以调用了
```



