animation 默认不会修改属性，动画完成后自动回到原来的属性；

form/to -> 0%/100%；



animation属性：

```javascript
animation-name: 需要绑定到选择器的keyframe名称;
animation-duration: 完成动画所花费的时间(ms/s);
animation-timing-function: 动画的速度曲线;
animation-delay: 动画开始之前的延迟;
animation-iteration-count: 动画播放的次数;
animation-direction: 是否应该轮流反向播放动画;
animation-fill-mode: 动画在播放之前或之后，其动画效果是否可见;
animation-play-state: 动画运行还是暂停；
```



```css
animation-iteration-count: n/infinite;
/* n次/无数次 */
```



```javascript
animation-direction: normal/reverse/alternate/alternate-reverse;
默认值，正常播放/反向播放/奇数次正向，偶数次反向/偶数次正向，奇数次反向;
```



```javascript
animation-fill-mode: none/forwards/backwards/both;
默认/
动画完成后保持完成后的效果(最后一个关键帧定义)/
在延迟时间内就应用属性值(第一个关键帧定义,默认不应用)/
向前向后填充模式都被应用
```



```javascript
animation-play-state:paused/running;
暂停/正常播放  //可以用js设定暂停按钮
```



animation事件：

```javascript
.animationstart = Fun; //动画开始时触发
.animationend = Fun; //动画结束时触发
```

