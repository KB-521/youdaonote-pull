生成器是ES6新增的一个极为灵活的结构，拥有在一个函数块内暂停和恢复代码执行的能力。



生成器对象也实现了Iterable接口，因此具有next()方法。

它默认的迭代器是自引用的（即只要调用了生成器函数就会生成迭代器）。



```javascript
// 定义生成器函数
function* generatorFn(){
    yield X; 
    yield Y;
    yield Z;
}

// 调用生成器函数会产生一个生成器对象
const generatorFnObject = generatorFn();
```

yield 关键字可以让生成器停止和开始执行。遇到yield 关键词后执行会停止，函数作用域的状态会被保留。停止执行的生成器函数只能通过在生成器对象上调用next()方法来恢复执行。



可以把生成器对象当成可迭代对象，使用for of关键词调用，使用起来会更方便：

```javascript
for (const x of generatorFn()) { 
    console.log(x); 
}
```



上一次让生成器函数暂停的yield关键字会接收到传给next()方法的第一个值：

```javascript
function* generatorFn(){
    return yield* "foo";
}

let generatorFnObject = generatorFn()

console.log(generatorObject.next()); // { done: false, value: 'foo' } 
console.log(generatorObject.next('bar')); // { done: true, value: 'bar' }
```



因为生成器对象实现了 Iterable 接口，而且生成器函数和默认迭代器被调用之后都产生迭代器，所以生成器格外适合作为默认迭代器。

```javascript
// 生成器作为默认迭代器
class Foo { 
    constructor() { 
        this.values = [1, 2, 3]; 
    }
    * [Symbol.iterator]() { 
        yield* this.values; 
    } 
}

// 还可以给对象加入迭代器
obj[Symbol.iterator] = function*(){
    yield XXX;
}
```



提前终止生成器:

```javascript
const g = generatorFn();
g.return();
g.throw();
// return()和 throw()方法都可以用于强制生成器进入关闭状态。
// 如果提供给return方法值，它就会成为迭代器终止时的值。
```



注：

1. 箭头函数不能来定义生成器；

1. 第一次调用next()传入的值不会被使用，因为这一次调用是为了开始执行生成器函数。

1. for-of 循环会无视done: true时返回的值；

1. 使用throw方法终止时，假如生成器函数内部处理了这个错误，那么生成器就不会关闭，而且还可以恢复执行。错误处理会跳过对应的 yield值，因此结果会跳过一个值。