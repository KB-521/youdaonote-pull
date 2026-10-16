定义：是一种一维的布局模型。他给flexbox的子元素之间提供了强大的空间分布和对齐能力；

默认情况下它会把超出部分等比压缩；

交叉轴(cross axis)与主轴(main axis)垂直；

只有直接子元素 会是弹性布局，“孙子”元素不会继承



设定元素为flex弹性盒子：

```javascript
display:flex;
```



主轴的方向(容器属性)：

```javascript
flex-direction: row/row-reverse/column/column-reverse;
//左到右方向(默认)/右向左方向/垂直，上往下/垂直，下往上
```



容器单线还是多线，以及新线堆叠方向(容器属性)：

```javascript
flex-wrap: nowrap/wrap/wrap-reverse;
//单行(默认)/多行/新线排在上面
```



在主轴上的对齐方式(容器属性)：

```javascript
justify-content: flex-start/flex-end/center/space-between/space-around;
//与main-start齐平(默认)/与main-end齐平/居中/两端对齐，每两个flex元素之间空隙相等/每个项目两侧距离相等;
```



在交叉轴上的对齐方式(容器属性)：

```javascript
align-items: flex-start/flex-end/center/baseline/stretch
//cross-start齐平(默认)/cross-end齐平/居中/元素的第一行文字基准对齐/元素未设置高度时,高度充满flex容器高度
```



交叉轴多线对齐方式，单线无效(容器属性):

```javascript
align-content: flex-start/flex-end/center/stretch/space-berween/space-around/auto;
//打包cross-start齐平/打包cross-end齐平/居中/未设置高度时占满整个交叉轴/cross两端对齐/每根轴两侧空隙相等/默认值
```



定义元素的main-size(元素属性)：

```javascript
flex-basis: length; //默认width/height
//主轴方向row/row-reverse时等于width
//主轴方向column/column-reverse时等于height
```



拉伸比例(元素属性)：

```javascript
flex-grow: number; //默认0
```



压缩比例(元素属性)：

```javascript
flex-shrink:number; //默认1 
//超出部分会自动压缩
//压缩尺寸 = flex-basis1*flex-shrink1 / (flex-basis1*flex-shrink1 + flex-basis2 * flex-shrink2) * 超出尺寸
```



单个项目在cross轴上对齐方式(元素属性)：

```javascript
align-self: flex-start/flex-end/center/baseline/stretch
//cross-start齐平(默认)/cross-end齐平/居中/元素的第一行文字基准对齐/元素未设置高度时,高度充满flex容器高度
```



排列位置(元素属性):

```javascript
order: number; 
//该项目排列的位置,number从小到大排列
```

