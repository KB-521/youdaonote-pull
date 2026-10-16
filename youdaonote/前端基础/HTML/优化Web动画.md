计时器做动画存在的问题：

1. 当前窗口不在动画页面时，计时器仍然在继续工作；

1. 回调函数执行如果耗时，会导致排队的情况，排队过多浏览器会崩溃；

1. 设置动画频率过高(计时器时间间隔短)，过度绘制，导致出现掉帧；



浏览器屏幕刷新频率大致 一秒60次 = 16.7ms一次；



requestAnimationFrame优势：

1. 当前窗口不在动画页面时，停止工作；

1. 浏览器刷新时自动执行，不需要手动设置间隔



requestAnimationFrame使用：

```javascript
var req = window.requestAnimationFrame(Fun);
// 屏幕每次刷新都会执行回调函数Fun
window.cancelAnimationFrame(req); //停止动画
```

注：H5新特性需要注意兼容问题；