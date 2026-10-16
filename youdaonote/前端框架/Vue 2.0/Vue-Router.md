定义路由：

```javascript
new vueRouter({
  routes: [
    {path: '/', component: 引入的页面}, 
    {path: '/user', component: 引入的页面}
  ],
  mode: "history" //定义url的匹配方式 默认哈希值匹配
})
new Vue({router: Router}).$mount('#app')
```

使用路由：

```javascript
<router-view></router-view> //路由匹配到的组件都会在里面
<router-link to="/"></router-link> //路由的跳转按钮,默认会渲染成a标签
this.$router.push('./'); //在js函数中使用此方法跳转
```

动态路由：

```javascript
routes: [
    // 动态路径参数 以冒号开头
    { path: '/user/:id', component: User }
]
children:{
    //子组件页面
    {path: '/user', component: 引入的页面}
}
$route.params //参数值会被设置的地方
```

监听路由：

```javascript
watch: {
    $route(to, from) {
    // 对路由变化作出响应...
}
to: 到那里去
from: 从哪里来
```

错误处理：

```javascript
path: '*',
redirect: {name: 'home'}
//无效的url都会进入这个页面
```

进度条：

```javascript
scrollBehavior(to,from,savePostion){
    //to,from: 去/来的网页,可以使用selector 找到锚点
    //savePostion 浏览器上一个网页的滚动条位置
    return {x:0, y:0} //横轴和纵轴的位置
}
```

路由守卫:

```javascript
//进入页面
router.beforeEach((to,from,next)=>{}) //全局守卫
//放在children的beforeEnter(to,from,next){} //局部守卫
beforeRouteEnter(to,from,next){} //在组件中的组件守卫
//离开页面
beforeRouteLeave(to,from,next){}
```



vueCli的本质还是webpack，所以可以使用import( )来进行异步加载；