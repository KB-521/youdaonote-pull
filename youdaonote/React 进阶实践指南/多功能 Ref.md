1. ref可以是一个对象或者回调函数，通过ref.current获取绑定的dom元素或者实例组件。

1. forwardRef 使用场景：

1. 组件想要获取子孙中的dom或者组件实例；

1. 函数组件没有实例，只能通过forwardRef；

1. 高阶组件是在原组件外层又包了一个组件，直接通过ref绑定ref.current会是高阶组件的实例而不是原组件，如果想要绑定原组件，可以使用forwardRef转发。

1. ref组件通信：ref绑定到类组件时，ref.current是组件实例，可以直接操作实例里的方法；对于函数组件可以用React.forwardRef和useImperativeHandle，自定义对外暴露的ref内容。

1. useRef：useRef返回的对象始终是不变的，改变current并不会导致组件重新渲染，可以利用这个特点去缓存数据。



在组件挂载时，更新dom后绑定ref；组件更新时，ref的指向如果改变，会在dom更新前将ref置空，更新dom后再绑定ref；组件卸载时ref也会置空。