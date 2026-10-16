 useMemo和useCallback区别

useCallback缓存钩子函数，useMemo缓存返回值。

每次更新都会重新调用一次函数创建组件，如果不使用这两个api缓存值，会造出内存浪费

 useState原理



 解释一下react 依赖收集

 promise原理

先定义三个状态 (pending，resloved，rejected)，定义resloved