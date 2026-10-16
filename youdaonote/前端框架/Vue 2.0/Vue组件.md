组件之间数据传输：

父组件 -》子组件：

```javascript
父:<app-datail :myName="name"></app-datail>
子: props: {
    "myName": {
        type: String, //规定数据类型
        // required: true, //是否能为空
        default: 'xiaoming' //默认值
    }
}
```

子组件 -》父组件：

```javascript
//自定义事件 推荐
<app-user-datail @changeParentName="changeName"></app-user-datail>
//父组件传回调函数,子组件调用
<app-user-datail :callback="callback"></app-user-datail>
```

子组件 -》子组件：

```javascript
通过父组件作用域调用 缺点:需要一级级的上传调用;
通过在main.js里创建全局的new Vue()调用;
```



slot:

```javascript
父:直接在自定义组件下写入HTML
子:<slot></slot> //调用父组件里写的HTML
注:两边的style下对组件定义的样式都有效;
父组件可以通过标签属性slot定义name，
子组件的slot里可以加入name="name"来限制显示的内;
如果子组件的name父组件里没有定义,就会显示子组件的内容;
```

component:

```javascript
<component :is="selectCom"></component>
//selectCom:子组件名称;
//根据变量selectCom可以定义标签里会显示哪个子组件;
//默认切换组件是注销重写,钩子函数destroyed会被触发;
<keep-alive></keep-alive>
//放入此标签里的component切换不会注销子组件,而是从缓存里调用组件;
//进入组件触发activated钩子函数;
//退出组件触发deactivated钩子函数;
```

