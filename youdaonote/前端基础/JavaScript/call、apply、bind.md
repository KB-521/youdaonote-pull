call、apply

定义：把函数临时赋值到对象上面执行。

区别：传递参数的形式不一样，call比apply的性能要好。

```javascript
function.call(obj,args1,args2) -> 一个个参数传递;
function.apple(obj,args) -> 数组的方式传递;
```



bind

定义：把函数拷贝一份并插入到对象作用域上面。

语法：

```javascript
obj.e = function.bind(obj,args1,args2);
```

bind实际干的事：

```javascript
obj.e = add
obj.e(2, 3)
delete obj.e
```



## 三者区别

1. 三者都可以改变函数的this对象指向。

1. 三者的第一个参数都是this要指向的对象，如果没有这个参数或参数为undefined、null，则默认指向都是全局window。

1. 三站都可以传参，但apply是数组，而call是参数列表，且apply和call是一次性传入参数，而bind可以分为多次传入。

1. bind是返回绑定this之后的函数，便于稍后调，apply和call则是立即执行。