## 基础准备

1. 在React中，executionContext代表了渲染期间的执行栈，也就是执行上下文。每当render过程中发生变化时，executionContext也会发生变化，因此可以通过它来判断当前render的状态。

1. 双缓冲技术(double buffering)：在ReactElement转换成fiber树这个过程中, 内存里会同时存在 2 棵fiber树, fiberRoot.current代表当前界面的Fiber树，而workInProgress则代表正在构造的Fiber树。构造完成之后重新渲染页面，最后切换这两个指向。

1. 优先级：

1. update优先级(update.lane)：它是一个环形链表，用来描述不同Update对象的优先级顺序。

> setState到底是同步异步

>     如果执行上下文executionContext为NoCotext，则会主动取消调度，并刷新回调，立即进入fiber树的构造过程，当执行下一段代码时，fiber树已经重新渲染了表现为同步。

>     正常情况下不会取消schedule调度，由于调度是通过MessageChanel触发(宏任务)，故体现为异步。

1. 渲染优先级(renderLanes)：每次render前，首先要确定render的优先级。它是一个全局概念，在fiber树构造过程中，只要fiber对象或者Update对象比渲染优先级低都会被忽略。

1. Fiber优先级(fiber.lanes)：Fiber.lanes和fiber.childLanes分别代表本节点和子节点的优先级。在构建fiber树的过程中，会使用renderLanes和fiber.lanes来判断该fiber节点是否需要更新，如果renderLanes不包含fiber.lanes，说明该fiber节点没有更新，此时可以复用，如果不能复用，就会进入创建阶段。

1. 栈帧管理：每次Fiber树的构造都是一个独立的过程，需要一组独立的全局变量。为了方便还原Fiber构造过程(比如实现时间切片)，React内部将这一独立的过程封装成一个栈帧Stack。

## 初次创建

1. 启动阶段

> 控制台打印Fiber树: document.getElementById('root')._reactRootContainer._internalRoot.current

1. 构造阶段：

1. 在执行Fiber构造前会先刷新栈帧prepareFreshStack。在这里创建了HostRootFiber.alternate，重置全局变量WorkInProgress和WorkInProgressRoot等。

1. 整个Fiber树的构造是一个深度优先遍历，在这个过程中React会维护两棵Fiber树，current和workInProgress分别是他们的指针。

1. current: 指向当前页面正在使用的Fiber节点；

1. workInProgress: 指向当前正在构建中的Fiber节点；

1. 在页面初始渲染时，由于页面还未渲染，因此current的值为null；

1. 在遍历中每个Fiber节点都会经历探寻阶段beginWork和回溯阶段completeWork。

1. 探询阶段 (针对所有Fiber类型，每一个case处理一个Fiber类型)：

1. 根据ReactElement对象创建所有的fiber节点，最终构造出fiber树结构。

1. 设置fiber.flags(二进制变量)，用来标记fiber节点的增删改状态，等待completeWork阶段处理。

1. 设置fiber.stateNode局部状态 (如Class类型节点: fiber.stateNode=new Class())。

1. 回溯阶段 (处理beginWork已经创建好的fiber节点)：

1. 调用componeteWork函数：

1. 给fiber节点创建DOM实例，设置fiber.stateNode的局部状态。

1. 为DOM节点设置属性和绑定合成事件。

1. 设置fiber.flags标记。

1. 把当前fiber对象的副作用队列 (firstEffect和lastEffect) 添加到父节点的副作用队列之后，更新父节点的firstEffect和lastEffect指针。

1. 识别beginWork阶段设置的fiber.flags，判断当前fiber是否有增删改，如果有需要将当前fiber加入到父节点的effects队列，等待commit阶段处理。

## 对比更新

1. 三种更新方式：

1. Class组建调用setState；

1. Funtion组件中调用hook对象暴露的dispatchAction；

1. 在container节点上重复调用render；

> 无论哪种方式最后都会间接调用scheduleUpdateOnFiber，它是输入链路中的必经之路。

1. 构造阶段会先找出fiber树中受到本次Update影响的所有节点，设置他们的fiber.lanes或fiber.childLanes供后续使用。

1. 探寻阶段不同处：

1. 如果是老节点，会对比渲染优先级和update优先级，如果无需更新进入bailout逻辑。

1. 最后会调用bailoutOnAlreadyFinishedWork对比子节点，都无需更新可以直接进入回溯阶段，如果需要更新会clone并返回子节点。

1. 给新增,移动,和删除节点设置fiber.flags(新增、移动: Placement，删除: Deletion)。

1. 如果是需要删除的fiber，出了自身打上Deletion之外，还要将其添加到父节点的effects链表中。

1. 回溯阶段在初次创建和对比更新中主要逻辑一致。

> 如果在更新过程中DOM属性有所变化，不会再次创建新的DOM对象，而是设置fiber.flags |= Update，等待commit阶段处理。