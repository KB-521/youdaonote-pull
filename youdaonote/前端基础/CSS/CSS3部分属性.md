圆角：

```javascript
border-radius:左上 右上 右下 左下; //长度
border-top-left-radius:x y; //左上(x轴长度,y轴长度)
border-top-right-radius:x y; //右上 
border-bottom-right-radius:x y; //右下 
border-bottom-left-radius:x y; //左下
```



盒子阴影：

```javascript
box-shadow:x y [模糊半径] [阴影拓展半径] [阴影颜色] [投影方式(内,外)];
```



文字阴影：

```javascript
text-shadow:x y [模糊半径] [模糊颜色];
```



文本颜色：

```javascript
rgba(红，绿，蓝，透明度); //子元素不继承透明度
opacity:0.5; //透明度，子元素会继承
```



线性渐变：

```javascript
linear-gradient(渐变方向(角度))，渐变颜色[百分比]);
//方向：to bottom/to bottom right,可以是角度: 0deg/45deg
```

径向渐变：

```javascript
radial-gradient(shape r/(a,b) at position,color[percent],color[percent])
//shape : 形状 circle(圆形)/cllipse(椭圆)
//r/(a,b) : 半径/长短轴
//position: 中心点位置(像素值/百分比/方向(yo left)/也可以是一个值，第二个值默认center)
```



单独设置每边的border值

```javascript
border:border-width border-style border-color;
//每边颜色也可单独设置
```



可添加border的背景图片：

```javascript
border-image:url number style;
//url:图片地址
//number: 图片裁剪的值
//style:图片添加的方式
```



input自定义轮廓：

```javascript
outline:outline-width outline-style outline-color;

/*用户获得焦点时轮廓改变*/
input:focus{
    outline:width style color;
}
```

