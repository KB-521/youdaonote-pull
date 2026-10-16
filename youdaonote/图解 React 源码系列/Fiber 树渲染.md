## fiber树特点

1. 无论是首次构造还是对比更新，最终都会在内存里输出一颗勇于渲染页面的fiber树(fiberRoot.finishedWork)；

1. 将要被渲染的fiber树特点：

1. 副作用队列挂载在根节点上(finishedWork.firstEffect)；

1. 代表最新页面的DOM对象挂载在fiber树的首个HostComponent类型节点上；

## commitRoot流程

1. 渲染前会做一些准备工作。

1. 设置全局状态；

1. 重置全局变量；

1. 再次更新副作用队列 (默认情况下副作用队列是不包括自身的，如果根节点有副作用，则把根节点添加到队列末尾。这里的操作只延长队列，不会改变lastEffect指针)；

1. 渲染会处理副作用队列，将最新的DOM节点渲染到界面上。

1. commitBeforeMutationEffects(dom变更前)：调用getSnapshotBeforeUpdate生命周期，清空#root容器节点，注册一个调度任务专门用来处理hook(所以hook都是异步执行)；

1. commitMutationEffects(dom变更)：处理DOM突变(新增、更新、删除)后调用react-dom包提供的直接操作DOM函数更新界面，更新root.current指向保证它指向最新的fiber树；

1. commitLayoutEffects(dom变更后)：调用componentDidMount或compoentDidUpdate生命周期，调用update.callback回调，设置一些原生状态(focus等)，重新设置ref；

1. 渲染后会做一些重置和清理工作。

1. 清除副作用队列；

1. 检测更新：

1. 在渲染过程中可能也会产生新的update(如在生命周期函数中setState);

1. 如果是常规(异步)任务，就把它注册到调度中心；

1. 如果是同步任务，就调用函数，主动再次进入Fiber树构造循环;