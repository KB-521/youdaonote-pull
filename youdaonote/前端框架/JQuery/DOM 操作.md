筛选：

```javascript
:odd/:even; //只能在css选择器中伪元素使用,筛选索引值奇/偶的元素
.first()/.last(); //筛选出第一个/最后一个元素
.eq(index); //筛选出索引为index的元素
.prev()/.prevAll(); //筛选出自己之前一个/全部的同级元素(自己不会被选择)
.next()/.nextAll(); //筛选出自己之后一个/全部的同级元素(自己不会被选择)
.siblings(); //筛选出除自己以外所有的同级元素
.fliter(cdn)/.not(cdn); //筛选出符合条件/不符合条件的元素(可以填函数)
.is(cdn); //判断符不符合条件,返回true.false
.map(function(index,ele){}); //遍历列表,返回值为return出的值
.has(cdn); //筛选出符合条件元素的父元素
```



查找：

```javascript
.children(selector); //查找符合条件元素的子元素
.find(cdn); //查找符合条件的后代元素
.end() = .prevObject; //查找自己的父级元素
.add(selector/element/jQuery Object/html); //拼接元素到对象
.addBack(); //拼接所有被选中的元素到对象(不常用)
.parent(selector); //查找符合条件元素的直接父元素
.parents(selector); //查找符合条件元素的直接祖先元素
.closest(selector/element/jQuery Object); //查找符合条件离自己最近的元素
.offetParent(); //查找最近的有设置定位的祖先元素(找到html为止)
```



插入：

```javascript
.before(html标签); //在同级元素后插入标签,返回同级元素
.insertBefore(同级元素); //在同级元素后插入标签,返回插入元素
.after(html标签); //在同级元素前插入标签,返回同级元素
.insertAfter(同级元素); //在同级元素前插入标签,返回插入元素
.append(html标签); //在父元素元素最后插入标签,返回父元素
.appendTo(父元素); //在父元素元素最后插入标签,返回插入元素
.prepend(html标签); //在父元素元素最前面插入标签,返回父元素
.prependTo(父元素); //在父元素元素最前面入标签,返回插入元素
```



替换：

```javascript
替换元素.replaceAll(被替换元素); //返回替换元素
被替换元素.replaceWith(替换元素); //返回被替换元素
```



删除：

```javascript
.empty(); //同等于.html(""); 删除选择的dom下全部后代元素
.remove(); //删除选择的元素并返回,不会返回事件上的方法
.detach(); // 删除选择的元素并返回,会返回事件上的方法
.clone(); // 克隆元素,默认不克隆方法,填入true克隆方法
// 重复克隆并不会不断添加,js指向那个就会添加那个
```



打包：

```javascript
.wrap(html结构); //将选中的dom每个外都添加html结构
.wrapAll(html结构); //将选中的dom添加到html结构,后续选择的结构会被修改到首个选中的结构处
.wraplnner(html结构); //给选中的dom下的子元素添加html结构
.unwrap(); //解除打包,不能解除html,head,body
```

