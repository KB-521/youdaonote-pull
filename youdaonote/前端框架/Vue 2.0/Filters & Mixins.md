Filters过滤器：

```javascript
局部:filters: {
    funName(value){
        //函数逻辑
    },
}
全局:Vue.filter('funName',(value)=>{
    //函数逻辑
})
使用场景:{{数据绑定 | 过滤函数}}、v-bind:指令|过滤函数
注:使用场景较少,无this指针,绝大多数情况使用计算属性更好
```



Mixins：

```javascript
Mixins.js:export default {vue中的script}
import Mixins from '.Mixins.js';
局部:mixins: [Mixins];
全局:Vue.mixin({Mixins});
//注:触发顺序:全局属性->局部属性->组件属性;    
//局部使用mixins类似深拷贝,每个文件的引用的属性都是独立的,互不干扰;
```

