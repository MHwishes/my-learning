# 和stash 相关

+ 查看git stash 的list

```
git stash list
```

+ 只取出某次stash 的内容（用上面命令查看序号）

` git stash apply 0`(0 是序号index)

+ 清空stash 的列表

```
git stash clear
```

# 和commit 相关

+ 撤销git add

```
 git reset HEAD <file>...
```

+ 撤销 git commit

1. `git reset --soft HEAD^`(代码任然保留，撤销commit,但不撤销add )

2. `git reset --mixed HEAD^`(代码任然保留,同时也撤销了git add)

3. `git reset --hard HEAD^ `(慎用，同时也撤销了git add，代码也被删除，恢复到上次commit 的状态)

# 重命名分支

1. 重命名本地分支：

`git branch -m oldBranch newBranch`

2. 删除远程分支（远端无此分支则跳过该步骤）

`git push --delete origin oldBranch`

3. 将重命名后的分支推到远端

`git push origin newBranch`

4. 把修改后的本地分支与远程分支关联

`git branch --set-upstream-to origin/newBranch`