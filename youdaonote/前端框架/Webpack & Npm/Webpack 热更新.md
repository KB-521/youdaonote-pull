> 热更新插件：webpack-dev-server, 

> webpack-dev-middleware + webpack-hot-middleware。



热更新原理：

1. 当修改了一个或多个文件。

1. 文件系统接收并通知webpack。

1. webpack重新编译构建一个或多个模块，并通知HMR服务器进行更新。

1. HRM Server 使用webSocket通知 HMR runtime 需要更新，HMR运行时通过HTTP请求更新jsonp；

1. HMR运行时替换更新中的模块，如果确定这些模块无法更新，则触发整个页面的刷新。