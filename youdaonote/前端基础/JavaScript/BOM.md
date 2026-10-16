BOM：浏览器对象模型，提供与浏览器交互的方法和接口；

全局变量全部存在window里面，window可以省略；

弹窗:

```javascript
(同步:阻断) 
alert("alert弹窗");

(同步:阻断 有返回值true/false)  
var bcf = confirm("confirm弹窗");

(同步:阻断 可以输入) 
var straf = prompt("prompt输入:","默认值");
```

导航栏：window.location

刷新页面：location.reload();

打开新的页面：location.replace("http://www.baidu.com/")

前进 后退按钮：history.forward()前进，history.back()后退，history.go(-∞/∞)前进后退几次；

浏览器信息：navigator；

获取浏览器分辨率：screen；



计时器:

循环执行:var sil = setInterval(函数名,时间);    

停止:clearInterval(sil);

一次执行:var sil = setTimeout(函数名,时间);   

停止:clearTimeout(sil);