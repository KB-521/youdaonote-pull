HTML5结构元素：

```javascript
<header>: 整个页面的头部,某块区域的标题，页眉;
<footer>: 文档或者某块的底部、页脚;
<main>: 主要的内容区域;
<nav>: 导航的连接部分;
<section>: 页面中一个内容区域;
<article>: 一个独立的、完整的相关内容块;
<aside>: 表示一个页面的一部分，它的内容跟这个页面的其他内容关联性不强，或没有关联，单独存在;
<figure>: 规定独立的流内容(图像、图表、照片、代码等等);
```



HTML5功能元素：

```javascript
video: 视频;
audio: 音频;
source: 资源; //可以在音频或视频中加入多个,这样如果上面的source无法运行就会自动变成下一个source
figcaption: 定义figure元素的标题;
canvas: 画布;
progress: 进度条;
```



HTML5表单：

新元素：

```javascript
radio: 单选圆点;
checkbox: 复选框;
text: 文本框;
password: 密码框;
file: 上传文件; //一次只能上传一个文件
tel: 电话; //触屏设备会直接跳出数字键盘,精准检测需要正则表达式
range: 可拖拽条;
number: 输入数字; //触屏设备会直接跳出数字键盘
email: 输入邮箱; //简单的检测,精准检测还需要正则表达式
date: 日期;
month: 月份;
week: 周;
time: 时间;
datetime-local: 日期和时间; //网页版选择不方便
color: 选择颜色;
```

新属性：

```javascript
multiple: file元素可以上传多个文件;
placeholder: 输入框提示;
pattern: 验证input类型输入框中内容是否与正则匹配;
```

