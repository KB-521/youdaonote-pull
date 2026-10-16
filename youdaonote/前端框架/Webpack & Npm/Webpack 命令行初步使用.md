1. 官网(https://webpack.docschina.org/)；

1. 安装环境 node

1. npm 包管理器，下载命令npm install(可能需要翻墙)，国内环境淘宝cnpm；

1. 生成项目说明书 npm init；

1. 下载webpack、webpack-cli；

1. webpack安装在node_modules文件夹下；

1. mode 生产模式和开发模式；

1. --watch 监听；

1. tree shaking去除死代码(没用到的自动删除)；

1. 将函数当做作用域；



devDependencies：开发依赖的库（--save-dev)；

dependencies：运行依赖的库 (--save)；



快速删除node_modules文件夹

```javascript
npm install rimraf -g
rimraf node_modules
```

