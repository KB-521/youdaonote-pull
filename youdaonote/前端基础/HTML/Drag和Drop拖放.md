HTML：

```javascript
draggable="true" //使标签元素变成可拖拽元素
```



拖放API：

```javascript
被拖拽元素.dragstart = fun; //开始被拖拽时触发
被拖拽元素.drag = fun; //在拖拽的过程中触发
被拖拽元素.dragend = fun; //在拖拽完成时触发
目标元素.dragenter = fun; //拖放元素进入目标元素时触发
目标元素.dragover = fun; //拖放元素在目标元素上时触发
目标元素.dragleave = fun; //拖放元素在目标元素上离开时触发
目标元素.drop = fun; //被拖放元素在目标元素上同时鼠标放开时触发
//注:需要阻止dragover的默认行为才会触发drop事件
e.preventDefault(); //阻止默认行为
```

DataTransfer对象：

```javascript
var dt = e.DataTransfer; //创建DataTransfer对象;
dt.setDate('id',元素.id); //向DataTransfer对象中存放数据
dt.getDate('id'); //向DataTransfer对象中读取数据
```



