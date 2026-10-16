安装&引入：

```javascript
yarn add react-redux --save
import {Povider, connect} from "react-redux"
```



概念：

1. Provider组件：自动的将store里的state和组件进行关联。

1. MapStateToProps：将store的state映射到组件的props里。

1. MapDispatchToProps：将store中的dispatch映射到组件的props里，实现了方法的共享。

1. Connect方法：将组件和数据(方法)进行连接。

注：MapStateToProps和MapDispatchToProps都是自定义映射函数，不是固定的方法。



使用：

```javascript
// 定义Reducer
function reducer(state={默认值},action){...}
const store = createStore(reducer)
// 定义 Action
const action = {...}
// 定义映射函数
function MapStateToProps (state) {
    // 映射参数
    return {value: state.num}
}
function MapDispatchToProps(dispatch) {
    // 映射方法
    return {onClick: () => dispatch(需要触发的Action函数)}
}
// 将组件和数据(方法)进行连接。
const App = connect(
    mapStateToProps,
)(组件名)
// 这时组件的props里就可以取到redux里的映射参数和映射方法了

// 挂载到ReacrDOM上
ReactDOM.render(
    <Provider store={store}>
        <App></App>
    </Provider>,
    document.getElementsById("root")
)
```

