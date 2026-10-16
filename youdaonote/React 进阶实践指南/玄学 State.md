1. setState执行流程：调用setState -> 计算优先级expirationTime -> 更新调度，调和fiber -> 合并state，执行render  ->  commit更新真实DOM  ->  执行回调函数 

1. 类组件对setState限制：pureComponent这一新的类，通过对state和props进行浅比较判断是否需要更新。shouldComponentUpdate(preState, preProps)生命周期函数，通过返回布尔值来决定是否更新。

1. setState原理：

```javascript
enqueueSetState: 创建一个update，然后放入当前的fiber对象的待更新队列中，最后开启调度更新。
batchedEventUpdates: 通过isBatchingEventUpdates标识开启batch更新。
unstable_batchedUpdates: 异步环境手动开启batch更新。
flushSync: 提升setState优先级
```

1. setState和useState区别：非pureComponent不会进行浅比较，只要调用setState就会更新，useState始终浅比较。setState有回调获取修改后的state。useState通过useEffect或者dispath执行后的副作用。setState倾向于合并，useState是替换。