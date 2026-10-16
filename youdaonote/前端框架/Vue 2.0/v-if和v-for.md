v-if条件判断：

```javascript
<v-if="">
<v-else-if="">
<v-else>
//注:如果在其他标签里不符合的不会加到浏览器dom中，
//<template>标签里不符合的还会加到浏览器dom中```



v-for循环：

```javascript
<v-for="(item,index) in arr">{{item | index}} 
//数组循环获取内容和序号
<v-for="(key,name,index) in obj">{{key | name | index}}
//对象循环获取值、键和序号

```

注:vue中的数组是通过栈名添加的，后续修改节点浏览器发现栈名没变，故浏览器页面内容不会修改，可以通过使用复制数组解决该问题。而.push()、.reverse()...等方法经过vue重构不会出现上述问题；



vue --version 查看vue-cli版本；