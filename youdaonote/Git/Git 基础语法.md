Git 设置用户名／邮箱：

```javascript
git config user.name '用户名'
git config user.email '邮箱'
```



Git 更新状态命令：

```javascript
git add // 追踪文件与暂存已经修改的文件
git commit '备注' // 提交更新
git commit --no-verify -m "备注"
git status // 查看状态
/ /查看修改:
git diff // 比较工作目录和暂存区
git diff -- staged // 比较暂存区和上一个版本
git diff HEAD // 比较工作目录和上一个版本
```



Git 查看提交历史：

```javascript
git log
```



Git 撤销：

```javascript
git checkout -- <file> //文件撤销到暂存版本
git reset HEAD <file> //撤销暂存区里的全部版本
```

