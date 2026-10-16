属性选择器：

```javascript
元素[属性];
元素[属性='val']  //属性值为'val'的元素
元素[属性~='val'] //属性有多个值，'val'为其中一个
元素[属性^='val'] //属性值以'val'开头的元素
元素[属性$='val'] //属性值以'val'结尾的元素
元素[属性*='val'] //属性值包含'val'的元素
```



同级选择器:

```javascript
元素1+元素2 //毗邻元素选择器，匹配所有紧随元素1之后的同级元素2
元素1~元素2 //兄弟选择器，匹配任何在元素1之后的同级元素2
```



伪类选择器：

```javascript
 :not(s)  //不含有s选择符的元素
 :first-child  //匹配父元素的第一个子元素
 :last-child  //匹配父元素的最后一个子元素
 :nth-child(n) //匹配父元素的第n个子元素
 :nth-last-child(n) //从后往前匹配父元素的第n个子元素
 :first-of-type  //匹配父元素同类型的第一个子元素
 :last-of-type  //匹配父元素同类型的最后一个子元素
 :nth-of-type //匹配父元素同类型的第n个子元素
 :nth-last-of-type //从后往前匹配父元素同类型的第n个子元素
:empty(dom树无内容) //匹配内容为空的元素
:enable  //匹配表单中激活的元素
:disabled  //匹配表单中禁用的元素
:checked  //匹配表单中被选中的radio(单选按钮)或checkbox(复选框)元素
:target //被选中值
:root  //根元素 (html、xml)
```



伪元素选择器(可以一个冒号也可以两个冒号)：

```javascript
:first-letter //设置对象内第一个字符的样式
:first-line  //设置对象内第一行的样式
:before
:after
::selection  //匹配用户当前选中的元素
```

