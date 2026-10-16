never类型是TS中的底层类型，他用来表示：

1. 一个从来不会有返回值的函数；

1. 一个总是会抛出错误的函数；

```typescript
function foo: never =(() => {
    throw new Error('Not Implemented')
})()
```



never仅能被赋值给另一个never类型；

与void类型区别：void表示没有任何类型，never表示永远不存在的值或者类型。

一个函数没有返回值是，他会返回一个void类型，但当一个函数根本没有返回值时(或者总是抛出错误)，他返回了一个never。

