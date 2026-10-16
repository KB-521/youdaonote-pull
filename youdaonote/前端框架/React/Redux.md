安装、引入redux：

```javascript
npm install redux --save
import {createStore, combineReducers} from "redux"
```



Reducers：

```javascript
// Reducer:
// 概念: 当前应用响应action后如何处理状态。
// 初始化的时候执行一次,并且每次更新数据也会执行。
const HandleNameReducer = (state = {初始化的值}, action)=>{
    switch(action.type){
        case "操作标识":
            action.自定义参数名 //取出自定义参数
            return {
                "需要修改的对象": "修改后的值"
            }
        default:
          return state //默认返回上一次state
    }
}
// 它是一个纯函数(函数式编程设计模式), 特点: 
// 1.输出的值只跟我们输入的值有关, 或者直接输出常量;
// 2.传入的值不能改变, 只能读取。

// Reducers:
// 一个Reducer最好只管理一个数据,再使用Reducers管理所有Reducer
const store = createStore(combineReducers({
    name: HandleNameReducer,
}))
```



Actions：

```javascript
const actionName = ({自定义参数名 = 自定义参数默认值} = {}) => {
    return {
        type: "操作标识", //必需
        "自定义参数名"
    }
}
// 减少dispatch()中的犯错
```



Store：

```javascript
// 返回应用当前的store树
store.getState()
// 更新redux: 就是让回调函数再执行一遍,并且把类型传过去
store.dispatch(actionName({
    "自定义参数名":"自定义参数值"
}))
// 监听器 每当 dispatch action的时候就会执行
store.subscribe(() => {
  // 一般写入重新渲染dom代码
})
```



redux的设计思想就是不产生副作用，数据更改的状态可回溯，所以redux中处处都是纯函数。