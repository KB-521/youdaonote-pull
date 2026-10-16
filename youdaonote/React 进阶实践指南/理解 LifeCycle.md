-  instance 类组件对应实例。

-  workInProgress 树，当前正在调和的fiber树，一次更新中，React会自上而下深度遍历自带fiber，如果遍历到一个fiber，会把当前fiber指向workInProgress。

-  current 树，在初始化更新中，current = null，在一次fiber调和之后，会将workInProgress赋值给current树。确保一次更新中，快速构建，并且状态不丢失。

-  Component 项目中的class组件。

-  nextProps 组件再一次更新中的新的props。

-  renderExpirationTime 下一次渲染的过期时间。



类组件：

1. 组件挂载时：constuctor（初始化state、绑定函数this、函数防抖）-> static getDerivedStateFromProps（根据prop、state返回新的state，返回null时state发生变化）-> render -> componentDidMount。

1. 组件更新时：static getDerivedStateFromProps -> shouldComponentUpdate(nextProps, nextState) => boolean（返回false不更新）-> render -> getSnapshotBeforeUpdate(prevProps, prveState)（在dom更新之前执行，返回值将作为第三个参数传递给componentDidUpdate）-> componentDidUpdate。

1. 组件卸载时：componentWillUnMount。



函数组件：

1. useEffect(cb, deps)：异步调用，会在试图绘制完毕后执行。在无依赖时，每次函数组件渲染都会运行cb；当依赖为[]时，仅会在挂载时运行；当存在依赖时，初始和每次依赖更新都会运行；cb返回的函数会在新cb运行前执行一次。

1. useLayoutEffect：使用方式和useEffect相似，但是是在Dom更新之后浏览器绘制之前调用cb，这样可以方便修改Dom，并且cb中的代码会阻塞浏览器绘制。

1. useInsertionEffect：使用方式和useEffect相似，执行时机在Dom更新前，可以用来解决CSS-in-JS导致重排和重绘问题。