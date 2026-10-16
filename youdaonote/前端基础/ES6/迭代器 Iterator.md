迭代器模式描述了一个方案，把实现了正式的Iterable接口的结构称为“可迭代对象”，他们可以通过迭代器Iterator消费。



检测结构是否实现了Iterable接口：

```javascript
function isIterable(item) {
  return !!item[Symbol.iterator]
}
```



实现Iterable接口的内置类型：

1. 字符串

1. 数组

1. 集合（Set）

1. 映射（Map）

1. arguments 对象

1. NodeList等DOM集合类型



传统循环缺陷:

for循环：理解比较困难，无法很好的管理变量 i ；

forEach/map: 无法使用 break 结束循环；

for in：理解比较困难，能遍历出不是当前索引的属性；



使用迭代器可以解决上面的问题：

```javascript
// 迭代器的实现
const arrs = []; // 任何实现Iterator接口的结构
const arrIterator = arrs[Symbol.iterator](); //调用迭代器
arr.next(); //依次返回相关对象
// 没有循环完返回 {value: "值", done: false}
// 循环结束返回 {value: undefined, done: true}
```



迭代器在日常中的一些使用处：

```javascript
for(let value of values) {}; // 遍历出每个values中的值,能使用break结束循环
arrs.keys()/values()/entries(); // 数组循环方法,返回一个带(所有索引/值/索引值对)的迭代器对象，最好配合for of使用
解构赋值，扩展运算符;
Array.from();
创建集合;
创建映射;
Promise.all()/Promise.race(); //接收由期约组成的可迭代对象
yield*操作符;
```



提前终止迭代器：

1. for-of 循环通过 break、continue、return 或 throw 提前退出。

1. 解构操作并未消费所有值：const [a,b] = [1, 2, 3] 。

