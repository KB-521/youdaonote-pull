useState

```typescript
const [数据, 更新数据的方法名] = useState(0);
// useState 可以传入函数,这样子就是惰性创建，只会被调用一次。
```



useEffect

```typescript
useEffect(() => {
    // 副作用函数
    // 相当于componentDidMount、componentDidUpdate 和 componentWillUnmount
    return () => {
        // 清除副作用函数
        // 组件销毁和每次更新组件都会优先调用
    }
},[count]); // 仅在count更新时更新
// 默认情况下会在每次渲染后调用副作用函数，包括第一次渲染
```



自定义hook：

```typescript
// 如果函数的名字以 “use” 开头并调用其他 Hook, 他就是一个自定义的hook
function useHookName(friendID) {
  const [isOnline, setIsOnline] = useState(null);
  useEffect(() => {
      // 副作用
    return () => {
      // 清除副作用
    };
  });
  return isOnline;
}
// 在其他的react组件中就可以进行复用hook了，两个组件都有不同的state
```



useContext

```typescript
const value = useContext(MyContext);
// 接收一个context对象(React.createContext 的返回值) 并返回该context的当前值。
// 当组件上层最近的<MyContext.Provider>更新时，该hook会触发重渲染,并使用最新传递给 MyContext provider 的 context value 值。
```



useReducer

```typescript
const [state, dispatch] = useReducer(reducer, initalArg, init);
// useState的代替方案, 接收一个reducer,并返回当前的state以及与其配套的dispatch方法。
```



useMemo

```typescript
const memoizedValue = useMemo(() => {changeName(name),[name]})
// 可以作为性能优化的一部分，只有当name改变时才会调用changeName
```



hook使用规则：

1. 只能在函数最外层调用hook，不能在循环、条件判断和子函数中调用。

1. 只能在react函数组件和自定义的hook中调用hook。