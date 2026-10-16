下载脚手架：

```javascript
npx create-react-app 文件名 
//注: 文件名不能有大写字母，npm版本要在5以上

npx create-react-app 文件名 --template typescript
// 新建ts react脚手架项目
```



脚手架的使用：

```javascript
// 入口文件 src/index.js
import React from "react"
import ReactDOM from "react-dom"
//注: 1.入口文件必需要引入react和reactDOM,html文件默认节点ID是root。
//2. 如果文件使用了jsx语法 必需引入react。
```



高级配置：

```javascript
// package.json配置代理
"proxy": "http://localhost:3000" //简单代理,后面是代理地址

// 自定义配置代理
// 1.安装http-proxy-middleware
// 2.

// .env自定义高级配置
https://www.html.cn/create-react-app/docs/advanced-configuration/
```

