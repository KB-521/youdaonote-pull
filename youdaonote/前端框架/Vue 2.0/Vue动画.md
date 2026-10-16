CSS动画：

```javascript
 <transition>需要添加动画的dom节点</transition>
//name定义style标签的开头;
//type定义按animation还是transition的结束时间为准;
//enter-...-class直接定义状态,不需要写style;
//一个transition标签里只能同时存在一个dom节点,
//v-if和v-else可以让一个transition标签切换存在,
//:key解决虚拟dom合并两个相同标签问题;
<style>
.v-enter{} //进入过渡的开始状态
.v-enter-active{} //进入过渡生效时状态
.v-enter-to{} //进入过渡的结束状态
.v-leave{} //离开过渡的开始状态
.v-leave-active{} //离开过渡生效时状态
.v-leave-to{} //离开过渡的结束状态
</style>
//生效状态中可以写animation和transition
```

JS动画：

```javascript
<transition
     @before-enter="beforeEnter" //进入中
     @enter="enter"
     @after-enter="afterEnter"
     @enter-cancelled="enterCancelled" //进入过程中失败
     @before-leave="beforeLeave" //离开时
     @leave="leave"
     @after-leave="afterLeave"
     @leave-cancelled="leaveCancelled" //离开过程中失败>
     需要添加动画的dom节点
</transition>
methods:{定义这8个函数}
//注:afterEnter和afterLeave必需调用done()才能结束进入下一过程
```

组件切换<component>也能用</transition>



列表动画：

```javascript
<transition-group tag="ul">
    <li></li>
</transition-group>
//tag: 定义由谁包裹li;
```

