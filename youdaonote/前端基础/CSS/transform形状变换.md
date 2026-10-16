一个元素css出现两个transform属性,下面的会覆盖上面的；

平移：

```css
transform:translate(x,y)/translateX(x)/translateY(y);
```



缩放：

```css
transform:scale(x,y)/scaleX(x)/scaleY(y);
```



旋转：

```css
transform:rotateX()/rotateY()/rotateZ();
/* rotate() = rotateZ() */
```



倾斜：

```css
transform:skew(x,y)/skewX(xdeg)/skewY(ydeg);
```



设置元素原点位置：

```javascript
transform-origin:X Y Z; 
//默认值:50% 50% 0;
//X轴方向: left/center/right/length/%;
//Y轴方向: top/center/bottom/length/%;
//Z轴方向: length;
```



启动gpu渲染：

```javascript
will-change: transfrom;
```

