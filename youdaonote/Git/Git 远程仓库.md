以本地仓库为基准：

```javascript
//在远程创建空仓库
git remote add <name> url //添加远程连接,name: 连接的别称
```

以远程仓库为基准：

```javascript
git clone url
```



多人协作：

```javascript
git fetch <name> //拉取
git merge <branch> //合并
git pull <name><branch> //拉取加合并 
git push <name><branch> //推送，连接的别称+分支名称
//pull和push都有缩写 通过git branch -vv查看链接在哪
```

