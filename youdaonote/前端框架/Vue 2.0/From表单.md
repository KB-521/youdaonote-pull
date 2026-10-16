v-model详解:

```javascript
v-bind:value = "value";
@input = "value = $event.target.value"
```



```javascript
<v-model.trim="value"> //去除空格
<v-model.lazy="value"> //失去焦点后才会修改data里的值
<v-model.number="value"> //只能输入数字
//复选框的双向绑定使用列表;
//单选框双向绑定一个变量就变成只能选择一个了;
//下拉菜单的select双向数据绑定一个变量就会默认选择那个变量;

//自定义组件也能使用双向数据绑定，
//子组件通过 props: ['value'] 取出数据，
//也可以通过自定义事件和回调函数修改父组件数据;
changeParent(value){
    this.$emit('input', value)
}
```

