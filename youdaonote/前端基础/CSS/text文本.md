字体间距：

```css
letter-spacing:1em;
```

空格的距离：

```css
word-spacing:16px;
```

书写顺序：

```javascript
direcion:ltr/rtl; //left to right/right to left
```

模仿<del>标签：

```javascript
text_decoration:none/line-through(中间穿过)/overline(上方穿过)/underline(下面穿过);
```

对齐方式:

```javascript
text-align:center/left/right/justify; //居中对齐/左对齐/右对齐/两端对齐
```

文字缩进:

```javascript
text-indent:2rem; //首行缩进两个字符
```



英文大小写字母装换：

```javascript
text-transform:uppercase(全大写)/lowercase(全小写)/capitalize(首字母大写);
```

换行：

```javascript
word-wrap:break-word; //到了边界强制换行
```

单行打点：

```javascript
white-space：nowrap; //文字不换行,直到碰到<br/>
overflow：hidden;  //多出来的文字不显示
text-overflow:ellipsis； //多出来文字加上省略号
```

多行打点：

```css
-webkit-line-clamp: 2; /*控制几行打点*/
text-overflow: ellipsis;
display: -webkit-box;
-webkit-box-orient: vertical; /*子元素被垂直排列*/
overflow: hidden; 
```

