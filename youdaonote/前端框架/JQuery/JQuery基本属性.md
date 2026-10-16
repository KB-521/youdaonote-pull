文本属性(不放元素查找，一个修改)：

```javascript
.text(); //相当于innerText 
//取值赋值均一组，可以放字符串和函数(index=索引值,ele=内容)
.heml(); //相当于innerHTML
//取值第一个，赋值一组，可以放字符串和函数
.val(); //相当于value
//取值第一个，赋值一组，可以放字符串，函数和数值
```



特性 属性(放一个元素查找，两个修改)：

```javascript
.attr(); //能定义出固有属性(特性)以及新增属性(自己定义的)
//取值第一个,赋值一组
.prop(); //只能定义出固有属性(特性)
//也能定义新增属性，不过不会定义到元素上只会在后台显示
//取值第一个,赋值一组,还能定义具体的值(比如:checked)
.removeAttr(); //能删除固有属性以及新增属性
.removeProp(); //只能删除用prop定义的新增属性
```



Class属性操作：

```javascript
.addClass(className); //给元素添加className
.removeClass(className); //给元素移除className
.hasClass(className); //判断元素有没有指定className,可以无视元素上其他的className
.toggleClass(className,false/true); //如果元素有className就移除，否则添加
// false/true:选填,只能移除/添加ClassName
```



CSS样式属性：

```javascript
.css(); //查询或修改具体样式,放数值查询多个样式，放对象修改多个样式(单位默认px)
.width()/height(); //查询或修改content宽度/高度(单位默认px)
.innerWidth()/innerHeight(); //content+padding宽度/高度
.outerWidth()/outerHeight(); //content+padding+border宽度/高度
//可以填入true查询content+padding+border+margin宽度/高度
//inner和outer都只能修改content大小,不会修改其他的
.offset(); //离文档而言的位置
.position(); //相对于最近的有定位的父级的位置
.scrollTop(); //上下滚动条距离最顶端的位置
.scrollLeft(); //左右滚动条距离最顶端的位置
```

