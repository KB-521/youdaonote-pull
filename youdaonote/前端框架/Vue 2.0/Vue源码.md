rollup打包工具，可以打包轮子。



1. package.josn文件dev脚本。scripts/config.js 找 web-full-dev 目标：入口文件 web/entry-runtime-with-compiler.js 出口文件 dist/vue.js。

1. 打包出来的三种模式 UMD | CommonJS | ES Module

1. 别名文件 scripts/alias.js

1. 真正入口文件地址 src/platforms/web/entry-runtime-with-compiler.js，文件暴露出Vue 实例，但没有Vue的定义，继续向下寻找。

1. => src/platforms/web/runtime/index,js

1. =>src/core/index.js

1. =>src/core/instance/index.js 寻找到Vue定义，就是一个构造函数：

```javascript
function Vue (option) {
    if(process.env.NODE_ENV !== 'production' &&
        !(this instanceof Vue)
    ) {
        warn('Vue is a constructor and should be called with the `new` keyword')
    }
    this._init(option)
}
```

1. 初始化Vue构造函数：

```javascript
initMixin(Vue) //Vue.prototype._init
stateMixin(Vue) //数据相关的方法, 如: Vue.prototype.$watch 
eventsMixin(Vue) //事件相关的方法, 如: Vue.prototype.$emit
lifecycleMixin(Vue) //生命周期相关的方法, 如: Vue.prototype.$destroy
renderMixin(Vue) //渲染相关的方法, 如: Vue.prototype._render
initGlobalAPI(Vue) //Vue构造函数上的全局方法, 如: Vue.mixin、Vue.componen、Vue.filter
Vue.prorotype.$mount // 挂载函数 会被重写为$el
```

