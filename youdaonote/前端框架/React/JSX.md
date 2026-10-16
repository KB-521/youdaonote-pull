JSX语法：

```javascript
const template = <div>dom节点</div> //这就是jsx
//注: 每个jsx最外面都要有个大节点套住，类似vue模版
```



渲染：

```javascript
//JXS中可以使用js表达式
const template = <div>{变量、函数、三部运算符...}</div>
//函数中可以直接return JSX语法
//注: Boolean类型、null、undefined不会被渲染。
```



注入到虚拟dom：

```javascript
const root = document.getElementById("app");
ReactDOM.render(template, root) //模版  需要注入的节点dom
```



React 是一个声明式，高效且灵活的用于构建用户界面的 JavaScript 库。

属性与事件：

```javascript
const template = <div id="a" className={js表达式}>dom节点</div>
//jsx上属性用法与html中无异,但是关键词有些会不同,可以去react官网查
const template = <button onClick={函数}>点击</button> //事件
//可以查询官网查看对应事件名称
```

注：

1. react中jsx引用值被修改浏览器中并不会自动更改，需要再调用ReactDom.render()。

2. jsx本身是一个对象，react会把新的jsx对象中的各个节点对象和老的jsx对象中的使用对比算法进行对比，只有不同的才会重新渲染。所以再渲染不会重置全部节点，而是选择性的重置改变的节点，从而大大节省性能。



数组渲染：

```javascript
 <ol>
    {
        obj.options.map((item,index) => {
            return <li key={`item${index}`}>{item}</li>
        })
    }
</ol>
```

注: 

1.渲染对象react会报错，渲染数组会将数组里全部的值全部按顺序渲染。

2.循环出的标签需要带上唯一key值, 不然其中的标签虚拟dom就会视为一个标签, 数组反转或者变换顺序就不会重新渲染。虽然每次都重新渲染有所损耗，但还是得不偿失。



总结一下就是key给每个Vnode一个唯一的id，可以依靠key更快更准确的拿到oldVnode	中对应的节点。

更准确：带key就不是就地复用了。

更快：利用key的唯一性生成map对象来获取对应的节点，比遍历方式更快。



