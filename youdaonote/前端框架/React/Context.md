Context 提供了一个无需为每层组件手动添加 props，就能在组件树间进行数据传递的方法。

API：

```javascript
const MyContext = React.createContext(defaultValue)
// 创建一个 Context 对象。
// 当React渲染一个订阅了这个Context对象的组件，这个组件会从组件树中离自身最近的那个匹配的Provider中读取到当前的context值。
// 如果没有匹配到时defaultValue值就会生效。
<MyContext.provider value={/* 值 */}
// 每个 Context 对象都会返回一个 Provider React 组件，它允许消费组件订阅 context 的变化。
MyContext.displayName = 'MyDisplayName'; //  context要显示的内容。
```

