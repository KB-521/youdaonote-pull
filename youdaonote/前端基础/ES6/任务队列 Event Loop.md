1. JS分为同步任务和异步任务；

1. 同步任务都在主线程上执行，形成一个执行栈；

1. 主线程外，事件触发线程管理着一个任务队列，只要异步任务有了运行结果，就在任务队列之中放置一个事件；

1. 一旦执行栈中所有的同步任务执行完毕，系统就会读取任务队列，将可运行的异步任务添加到可执行栈中，开始执行。

![](images/B5A5A44E4EAA475B8014E8D88A61EF9Ajpg)

每个任务都有个任务源，源自同一个任务源的task必须放到同一个任务队列，从不同源来的则被添加到不同队列。



宏任务 Macrotask：

特点：会在一个(macro) task执行结束后，在下一个(macro) task 执行开始前，对页面进行重新渲染。

```javascript
MacroTask(/* 宏任务 */) 主要包括:
script(整体代码)、setTimeout、setInterval、
setImmediate(Node)、requestAnimation(浏览器)、
IO、UI rendering
```



微任务 Microtask：

特点：他的响应速度相比宏任务会更快，因为他不需要等待渲染。在某个宏任务执行完后，就会在他执行期间产生的所有的微任务都执行完毕（在渲染前）。

```javascript
Microtask(/* 微任务 */)包括:
process.nextTick(/* Node */)、Promise、Object.observe、
MutationObserver
```



运行机制： 

- 执行一个宏任务（栈中没有就从事件队列中获取）

- 执行过程中如果遇到微任务，就将它添加到微任务的任务队列中

- 宏任务执行完毕后，立即执行当前微任务队列中的所有微任务（依次执行）

- 当前宏任务执行完毕，开始检查渲染，然后GUI线程接管渲染

- 渲染完毕后，JS线程继续接管，开始下一个宏任务（从事件队列中获取）

![](images/FBBC9FEBF6184F3D835FF886ABA05039jpg)

await做了什么：

await是一个让出线程的标志。await后面的表达式会先执行一遍，将await后面的代码加入到microtask中，然后就会跳出整个async函数来执行后面的代码。

