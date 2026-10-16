1. 原型链继承

```javascript
function SuperType() {
  this.property = true;
} 

function SubType() {
  this.subProperty = false; 
}
// 继承SuperType
SubType.prototype = new SuperType()
// 注：子类添加方法必需在原型赋值后添加到子类的原型上。
```

### 存在的问题：

- 原型中包含引用值会在所有的实例间共享。

- 子类在实例化时不能给父类传参数。



1. 盗用构造函数

```javascript
function SuperType(name) {
  this.name = name;
} 

function SubType() {
  // 继承 SuperType 并传参
  SuperType.call(this, "king")
  // 实例属性
  this.age = 29;
}
```

### 存在的问题：

- 必需在构造函数中定义方法，函数不能重用。

- 子类不能访问父类原型上定义的方法。



1. 组合继承

```javascript
function SuperType(name) {
  this.name = name;
} 

function SubType(){
  // 继承属性
  SuperType.call(this, "king")
}
// 继承方法
SubType.prototype = new SuperType()
```

#### 组合继承弥补了原型链和盗用构造函数的不足，是JavaScript中使用最多的继承。



1. 原型式继承

```javascript
function object(o){
  function F()
  F.prototype = o
  return new F()
}

let person = {
 name: "king"
}; 

// 继承person
let anotherPerson = object(person);

// ES6新增Object.create()方法, 他的效果和object()方法相同
let yetAnotherPerson = Object.create(person);
```

原型式继承适合在不需要单独创建构造函数，但仍然需要在对象间共享信息的场合。

他属性中包含的引用值始终会在相关对象直接共享。



1. 寄生式继承

```javascript
function createAnother(original){
  let clone = Object.create(original)
  // 新增属性和方法
  clone.fn = function() {}
  return clone
}

// 例子: 
let person = {
 name: "king"
}; 
// 继承person
let anotherPerson = createAnother(person);
```

寄生式继承同样适合主要关注对象, 而不在乎类型和构造函数的场景。

和构造函数模式类似，通过寄生式继承给对象添加函数会导致函数难以重用。



1. 寄生式组合继承

```javascript
function inheritPrototype(subType, superType) {
  let prototype = Object.create(superType.prototype); // 创建对象
  prototype.constructor = subType; // 增强对象
  subType.prototype = prototype; // 赋值对象
} 

// 例子: 
function SuperType(name) {
 this.name = name;
} 
// 继承SuperType
function SubType(){
  SuperType.call(this, "king")
}
inheritPrototype(SubType, SuperType)
```

寄生式组合继承只需要调用一次SuperType构造函数，避免了SubType.prototype上不一样也用不到的属性，可以说比组合式继承效率更高。

寄生式组合继承算是引用类型继承的最佳模式。