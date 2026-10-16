window对象通过history对象提供对浏览器历史记录的访问能力，而在HTML5中还可以操纵历史几率中的数据；

```javascript
history.back(); //后退一级
history.forword(); //前进一级
history.go(num); //前进num级(输入负数则为后退)
history.length; //查看当前页面放了多少历史记录

history.pushState(stateObj,'page','bar.html'); //添加一条历史记录
history.replaceState(stateObj,'page','bar.html'); //替换当前历史记录
//stateObj: 可以上传到新页面的对象
//page: 历史记录名称,暂时没用,填入''即可
//bar.html: 新打开的页面

wiondow.onpopstate=Fun; //当历史记录发生变化使会触发
//注: .pushState和.replaceState不会触发此事件
e.state.data; //存储stateObj的位置
```



ajax是直接刷新页面，导致页面无历史记录；

.pushState和.replaceState能解决无刷新历史记录切换问题