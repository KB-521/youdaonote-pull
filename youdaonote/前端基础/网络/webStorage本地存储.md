localStorage 永久数据(除非用户本地删除)，

sessionStorage 临时数据；

存取的是字符串类型，可以存更大的数据(5MB);



Storage：

```javascript
//添加
localStorage.user = '';
localStorage.obj = JSON.stringify(obj); //对象要JSON格式
//读取
localStorage.user;
JSON.parse(localStorage.obj)
localStorage.setItem('id',123); //添加
localStorage.getItem('id'); //读取
localStorage.remove('id'); //删除id字符串
localStorage.clear(); //删除全部数据
```



localStorage数据必需同源才能共享；

sessionStorage数据必需同源和同窗口才能共享；

