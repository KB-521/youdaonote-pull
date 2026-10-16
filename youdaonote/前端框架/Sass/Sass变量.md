变量：

```javascript
$变量名: 值; //变量
@import "src"; //引入其他scss文件
```

变量的类型：数字，颜色，字符串，Null，布尔值；

注释：/* */，// 都是Sass中注释的方法，区别是前者会出现在编译后的css文件中，后者则不会；

如果样式的属性是 null 那么此样式在编译后就会移除;



mixin：

```javascript
//_mixin.scss 文件
@mixin name($color:默认值,$color2:默认值){
    //()内可以接收传入的值,并放在变量$color中
    color: $color;
    @content; //取出传入的样式
}
//主文件
@import "mixin.scss"; //引入写了mixin.scss文件
@include name(red){ 
 //()内可以传值,也可以写 变量名: 属性 格式,指定要传入哪个属性
    background: green; //传入样式
}
```

