> React中Context提供了直接访问祖先节点的状态的方法，避免多级组件层层传递props。

## 创建 Context

1. 通过React.createContext这个api创建context对象。

1. createContext核心逻辑：

1. 初始值保存在context._currentValue中 (同时保存在context._currentValue2中，支持多个渲染器并发渲染)。

1. 同时创建context.Provider和context.Consumer2个reactElement对象。

## 消费 Context

1. 3种消费Context方式：

1. 使用MyContext.Consumer组件 (不推荐)；

1. class组件中，使用静态属性contextType获取context；

1. function组件中，使用useContext获取context；

> 3种方式只是react根据不同场景封装的api，内部核心的实现是一样的。

1. 核心逻辑：

1. prepareToReadContext：设置全局变量，为readContext做准备；

1. readContext：返回context._currentValue，并构造一个contextItem加入到workInProgress.dependencies链表之后 (用于在更新时使用，判断是否依赖了Context.Provider中的值)。

## 更新 Context

1. 组件更新后先检查value是否有没有改变，没改变进入bailout(判断子树节点是否可以完全复用)。

1. value改变后：

1. 先从ContextProvider类型节点开始向下遍历，查找所有被fiber.dependencies依赖的context节点；

1. 再从这些节点开始向上遍历，修改父路径上所有节点的fiber.childLanes属性，表明其子节点有改动，子节点会进入更新逻辑；