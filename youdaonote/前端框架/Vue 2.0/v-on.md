v-on: 可以给标签绑定事件；

```javascript
<v-on:click="Fun"> //可以直接写函数名也可以执行函数;
//直接写函数名默认传入事件对象
//执行函数可以传入实参,并传入$event来使函数获取事件对象
```



事件修饰符：

```javascript
<v-on:click.stop> //取消冒泡
<v-on:click.prevent> //取消事件默认行为
```

按键修饰符：

```javascript
<v-on:keyup.enter> //必需按下Enter才能触发
//也可以用按键的which值
```

事件修饰符和按键修饰符都可以连续调用；



v-on:可以简写成 @ ；

v-bind:可以简写成 : ；

