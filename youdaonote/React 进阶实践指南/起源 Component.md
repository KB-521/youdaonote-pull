1. 组件的本质就是UI + 更新视图方法 + 普通的类和函数；

1. 类组件底层只需要实例化一次，实例中保存了组件的state等状态。对于每一次更新只需要调用render方法以及对应的生命周期就可以了。但函数组件每次都是都是一次新的函数执行，一次函数组件的更新，里面的变量会重新生成。

1. 组件通信方式：

```javascript
1. props和callback方式
2. ref方式
3. React-redux或React-mobx 状态管理方式
4. context上下文方式
5. event bus事件总线
```

1. 组件强化方式：HOC、自定义hooks



