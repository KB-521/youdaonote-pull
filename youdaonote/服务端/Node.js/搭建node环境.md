1. npm init 或者 yarn init 新建项目

2.引入babel

```javascript
yarn add @babel/cli @babel/core @babel/preset-env --dev
```

3.配置.babelrc文件

```javascript
{
  "presets": [
    ["@babel/preset-env", {
      "targets": { //此项可以写上环境,babel会无视此环境已经适配的js语法
        "node": "current" 
      }
    }]
  ]
}
```

4.安装nodemon和rimraf

```javascript
yarn add nodemon --dev // 在受监听文件变化时自动执行node
yarn add rimraf --dev // 删除指定文件
```

5.配置nodemon.json

```json
{
  "watch":[
    需要监听的路径，文件
  ],
  "ignore":[
    无视的文件，文件夹，后缀名
  ]
}
```

6.配置package.json下的scripts

```javascript
"scripts": {
    "build": "babel src --out-dir dist", //打包
    "start": "node dist/index", //node执行打包后的文件
    "restart": "rimraf dist && yarn build && yarn start",
    //先删除原有文件夹，再打包，在执行node
    "dev": "nodemon --exec yarn restart"
    // 使用nodemon进行监听，如有改变执行restart
}
```

7. 运行

```javascript
yarn dev
```

注: node需要有一个执行的主文件，在里面引用其他文件