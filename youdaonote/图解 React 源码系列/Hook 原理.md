## 概念

1. Hook对象属性：

1. hook.memoizedState: 保存在内存中的局部状态；

1. hook.baseState: hook.baseQueue中所有的update对象合并之后的状态；

1. hook.baseQueue: 存储update对象的环形链表，只包括高于本次渲染优先级的update对象；

1. hook.queue: 存储update对象的环形链表，包括所有优先级的update对象；

1. hook.next: next指针，指向链表的下一个hook；

1. 状态Hook：广义只要实现数据持久化且没有副作用的hook，均可视为状态Hook(useState、useReducer、useContext、useRef、useCallback、useMemo)。

> useState是useReducer的建议封装。

1. 副作用Hook：会修改fiber.flags(会在fiber构造阶段加入到副作用队列，最后在commitRoot阶段处理这些副作用)。

> 在React内部，useEffect就是最标准的副作用Hook，其他自定义hook，如果需要实现副作用，必须直接或者间接调用useEffect。

1. Function组件流程

1. 调用function前:  设置全局变量，标记渲染优先级和当前fiber，清除当前的fiber遗留状态。

1. 调用function：构造出Hook链表，最后生成子级ReactElement对象(children)。

1. 调用function后：重置全局变量(保证不同的function节点在调用renderWithHooks互不影响)，返回children。

> Hook数据持久化原理：

> 1. 通过双缓存技术为基础，将current.memoizedState按照顺序克隆到了workInProgress.memoizedState中；

> 2. Hook经过一次克隆，内部的属性hook.memoizedState等都没有变动，所以其状态不会丢失；

## 状态Hook

1. mountState(useState)和mountReducer(useReducer)：主要负责创建hook、初始化hook属性、最后返回[当前状态, dispatch函数]。

1. mountState使用的是内置的reducer，mountReducer使用外部传入reducer，可见useState就是useReducer的基本封装。

1. 在useState函数内部，初始状态同时保存在了hook.memoizeState和hook.baseState中：

1. hook.memoizeState：当前状态；

1. hook.baseState：基础状态，作为合并hook.baseQueue的初始值；

1. 状态更新：

1. 获取workInProgressHook对象；

1. 拼接链表：将hook.queue.pending拼接到current.baseQueue；

1. 状态计算：

1.  update优先级不够，加入到baseQueue中，等待下一次render；

1. update优先级足够，状态合并；

1. 更新属性；

> 同时执行多次dispatch，会请求多次调度，由于调度中心的节流优化，最后只会执行一次渲染。

1. 性能优化

1. 如果上次renducer函数存在，则使用它和当前action计算出eagerState(本次渲染状态)，如果eagerState和上次渲染状态相同则不需要更新(update已经被挂载到queue.pending，没有丢弃下次update需要的时候还是会起作用)。

1. 在React17.x前还是采取同步更新模式，React18.x中进入全面异步更新模式：

1. 在这个模式下将更新队列拆分为多个子队列，按照优先级顺序进行更新，提高应用的性能和响应速度；

1. baseQueue和baseState对象则用于存储更新对象和状态值，并确保每个更新对象都被正确地分配到适当的子队列中，以便优先级更高的更新能够更快地得到处理；

## 副作用Hook

1. mountEffect(useEffect)和mountLayoutEffect(useLayoutEffect)内部都是直接调用mountEffectImpl，只是参数不fiber.flags和effect.tag不同。

> mountEffectImpl逻辑：

> 创建Hook；

> 设置workInProgress的副作用标记：flags |=fiberFlags；

> 创建efffect对象，挂载到hook.memoizedState上；

1. 处理effect回调：

1. workInProgress.flags打上了标记，Effect回调会在fiber树渲染阶段的commitRoot函数中处理：

1. dom变更前：处理副作用队列里带Passive标记(由useEffect创建)的fiber节点，其中的flushPassiveEffects的由调度中心处理，所以是异步回调并不会马上执行。

1. dom变更，界面更新：处理useLayoutEffect()创建的effect，同步调用effect.destroy()。

1. dom变更后：处理useLayoutEffect()创建的effect，调用effect.create(用户传入的回调)将返回值赋值给effect.destory；把有副作用的fiber中带有Passive标记的effect筛选出来，添加到一个全局数组。

1. flushPassiveEffects可以脱离fiber节点，直接访问上述添加到全局数组的effect：

1. 遍历pendingPassiveHookEffectUnmount中所有的effect，调用effect.destory()，同时清空数组；

1. 遍历pendingPassiveHookEffectMount中的所有effect，调用effect.create()并把返回值赋值给effect.destory，同时清空数组；

1. 初次调用后发起更新，更新effect回调：

1. 如果依赖没变，新建Hook(effect.tag不含HookHasEffect)；

1. 如果依赖改变, 更改fiber.flag, 新建effect。

> 只有effect.tag包含HookHasEffect时才会调用effect.destory和effect.create；

> 无论依赖是否变化, 都复用之前的effect.destroy；

1. 组件销毁时fiber.flag打上Deletion标记，在dom变更阶段的commitDeletion中执行effect.destroy()，结束整个闭环。


